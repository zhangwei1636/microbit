UART 串口
****

.. py:module:: microbit.uart

The ``uart`` module lets you talk to a device connected to your board using
a serial interface.

uart模块允许与连接到板上串口的设备通信。


Functions 函数
=========

.. method:: init(baudrate=9600, bits=8, parity=None, stop=1, \*, tx=None, rx=None)

    Initialize serial communication with the specified parameters on the
    specified ``tx`` and ``rx`` pins. Note that for correct communication, the parameters
    have to be the same on both communicating devices.

    用指定的参数初始化tx和rx引脚的串行通信参数。注意，为了正确通信，两个设备的通信参数必须设为一样。

    .. warning::

    警告：

        Initializing the UART on external pins will cause the Python console on
        USB to become unaccessible, as it uses the same hardware. To bring the
        console back you must reinitialize the UART without passing anything for
        ``tx`` or ``rx`` (or passing ``None`` to these arguments).  This means
        that calling ``uart.init(115200)`` is enough to restore the Python console.

        当使用相同的硬件时，在外部引脚上初始化UART将导致USB上的Python控制台无法访问。 要使控制台恢复原状，必须重新初始化UART，而不给tx或rx传递任何内容（或将None传递给这些参数）。 这意味着调用uart.init（115200）足以恢复Python控制台。

    The ``baudrate`` defines the speed of communication. Common baud
    rates include:

    baudrate定义了通信速度。一般波特率包括：

        * 9600
        * 14400
        * 19200
        * 28800
        * 38400
        * 57600
        * 115200

    The ``bits`` defines the size of bytes being transmitted, and the board
    only supports 8. The ``parity`` parameter defines how parity is checked,
    and it can be ``None``, ``microbit.uart.ODD`` or ``microbit.uart.EVEN``.
    The ``stop`` parameter tells the number of stop bits, and has to be 1 for
    this board.

    bits定义了传送字节的长度，本板只支持8位。parity参数定义了奇偶校验方式，有三种方式：None、microbit.uart.ODD、microbit.uart.EVEN。stop设置停止位，本板设置为1位停止位。

    If ``tx`` and ``rx`` are not specified then the internal USB-UART TX/RX pins
    are used which connect to the USB serial converter on the micro:bit, thus
    connecting the UART to your PC.  You can specify any other pins you want by
    passing the desired pin objects to the ``tx`` and ``rx`` parameters.

    如果未指定tx和rx，则使用内部USB-UART TX / RX引脚连接到micro：bit上的USB串行转换
    器，从而将UART连接到PC。 您可以通过将所需的引脚对象传递给tx和rx参数来指定所需的任
    何其他引脚。

    .. note::

    注意：

        When connecting the device, make sure you "cross" the wires -- the TX
        pin on your board needs to be connected with the RX pin on the device,
        and the RX pin -- with the TX pin on the device. Also make sure the
        ground pins of both devices are connected.

        连接设备时，请确保电线的交叉连接-板上的Tx引脚需要与设备上的Rx引脚连接，板上的Rx引脚需要与设备上的Tx引脚连接。还要确保板与设备的接地引脚已经连接。


.. method:: uart.any()

   Return ``True`` if any data is waiting, else ``False``.

   如果uart口有数据等待处理，则返回True，否则返回False。

.. method:: uart.read([nbytes])

    Read bytes.  If ``nbytes`` is specified then read at most that many
    bytes, otherwise read as many bytes as possible.

    读取字节。如果指定了nbytes，则读取的字节数最多为该字节，否则读取的字节数尽可能多。

    Return value: a bytes object or ``None`` on timeout.

    返回值：一个字节对象或超时时无。

    A bytes object contains a sequence of bytes. Because
    `ASCII <https://en.wikipedia.org/wiki/ASCII>`_ characters can fit in
    single bytes this type of object is often used to represent simple text
    and offers methods to manipulate it as such, e.g. you can display the text
    using the ``print()`` function.

    字节对象包含一系列字节。因为ASCII字符是单个字节，所以这种类型的对象通常用于表示简单文本，并提供相应的操作方法，例如，可以使用print（）函数显示文本。

    You can also convert this object into a string object, and if there are
    non-ASCII characters present the encoding can be specified::

    还可以将此对象转换为字符串对象，如果存在非ASCII字符，则可以指定编码：

        msg_bytes = uart.read()
        msg_str = str(msg, 'UTF-8')

    .. note::

    注意：

        The timeout for all UART reads depends on the baudrate and is otherwise
        not changeable via Python. The timeout, in milliseconds, is given by:

        所有UART读取的超时取决于波特率，亦不能通过python更改。超时时间（以毫秒为单
        位）由以下公式给出：

        ``microbit_uart_timeout_char = 13000 / baudrate + 1``

    .. note::

    注意：

        The internal UART RX buffer is 64 bytes, so make sure data is read
        before the buffer is full or some of the data might be lost.

        内部UART RX缓冲区为64字节，因此请确保在缓冲区满之前读取数据，否则可能会丢失某些数据。

    .. warning::

    警告：

        Receiving ``0x03`` will stop your program by raising a Keyboard
        Interrupt. You can enable or disable this using
        :func:`micropython.kbd_intr()`.

        接收0x03将产生键盘中断来停止程序。 您可以使用启用或禁用此功能：micropython.kbd_intr()

.. method:: uart.readall()

    Removed since version 1.0.

    从版本1.0移去此方法。

    Instead, use :func:`uart.read()` with no arguments, which will read as much data
    as possible.

    用无参uart.read()函数来代替。它可以读尽可能多的数据。

.. method:: uart.readinto(buf[, nbytes])

   Read bytes into the ``buf``.  If ``nbytes`` is specified then read at most
   that many bytes.  Otherwise, read at most ``len(buf)`` bytes.

   读字节数到缓冲区buf中。如果指定了nbytes，则读取nbytes指定的字节数，否则读取缓冲区buf大小的字节数。

   Return value: number of bytes read and stored into ``buf`` or ``None`` on
   timeout.

   返回值：读或写入缓冲区buf的字节数值，超时则返回None。

.. method:: uart.readline()

   Read a line, ending in a newline character.

   读一行，以换行符结尾。

   Return value: the line read or ``None`` on timeout. The newline character is
   included in the returned bytes.

   返回值：读取的行，超时返回None。换行符包括在返回的字节中。

.. method:: uart.write(buf)

    Write the buffer to the bus, it can be a bytes object or a string::

    写缓冲区数据到总线上，它可以是字节对象或字符串：

        uart.write('hello world')
        uart.write(b'hello world')
        uart.write(bytes([1, 2, 3]))

    Return value: number of bytes written or ``None`` on timeout.

    返回值：写入的字节数，超时返回None。
