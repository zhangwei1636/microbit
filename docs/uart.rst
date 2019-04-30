UART ����
****

.. py:module:: microbit.uart

The ``uart`` module lets you talk to a device connected to your board using
a serial interface.

uartģ�����������ӵ����ϴ��ڵ��豸ͨ�š�


Functions ����
=========

.. method:: init(baudrate=9600, bits=8, parity=None, stop=1, \*, tx=None, rx=None)

    Initialize serial communication with the specified parameters on the
    specified ``tx`` and ``rx`` pins. Note that for correct communication, the parameters
    have to be the same on both communicating devices.

    ��ָ���Ĳ�����ʼ��tx��rx���ŵĴ���ͨ�Ų�����ע�⣬Ϊ����ȷͨ�ţ������豸��ͨ�Ų���������Ϊһ����

    .. warning::

    ���棺

        Initializing the UART on external pins will cause the Python console on
        USB to become unaccessible, as it uses the same hardware. To bring the
        console back you must reinitialize the UART without passing anything for
        ``tx`` or ``rx`` (or passing ``None`` to these arguments).  This means
        that calling ``uart.init(115200)`` is enough to restore the Python console.

        ��ʹ����ͬ��Ӳ��ʱ�����ⲿ�����ϳ�ʼ��UART������USB�ϵ�Python����̨�޷����ʡ� Ҫʹ����̨�ָ�ԭ״���������³�ʼ��UART��������tx��rx�����κ����ݣ���None���ݸ���Щ�������� ����ζ�ŵ���uart.init��115200�����Իָ�Python����̨��

    The ``baudrate`` defines the speed of communication. Common baud
    rates include:

    baudrate������ͨ���ٶȡ�һ�㲨���ʰ�����

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

    bits�����˴����ֽڵĳ��ȣ�����ֻ֧��8λ��parity������������żУ�鷽ʽ�������ַ�ʽ��None��microbit.uart.ODD��microbit.uart.EVEN��stop����ֹͣλ����������Ϊ1λֹͣλ��

    If ``tx`` and ``rx`` are not specified then the internal USB-UART TX/RX pins
    are used which connect to the USB serial converter on the micro:bit, thus
    connecting the UART to your PC.  You can specify any other pins you want by
    passing the desired pin objects to the ``tx`` and ``rx`` parameters.

    ���δָ��tx��rx����ʹ���ڲ�USB-UART TX / RX�������ӵ�micro��bit�ϵ�USB����ת��
    �����Ӷ���UART���ӵ�PC�� ������ͨ������������Ŷ��󴫵ݸ�tx��rx������ָ���������
    ���������š�

    .. note::

    ע�⣺

        When connecting the device, make sure you "cross" the wires -- the TX
        pin on your board needs to be connected with the RX pin on the device,
        and the RX pin -- with the TX pin on the device. Also make sure the
        ground pins of both devices are connected.

        �����豸ʱ����ȷ�����ߵĽ�������-���ϵ�Tx������Ҫ���豸�ϵ�Rx�������ӣ����ϵ�Rx������Ҫ���豸�ϵ�Tx�������ӡ���Ҫȷ�������豸�Ľӵ������Ѿ����ӡ�


.. method:: uart.any()

   Return ``True`` if any data is waiting, else ``False``.

   ���uart�������ݵȴ������򷵻�True�����򷵻�False��

.. method:: uart.read([nbytes])

    Read bytes.  If ``nbytes`` is specified then read at most that many
    bytes, otherwise read as many bytes as possible.

    ��ȡ�ֽڡ����ָ����nbytes�����ȡ���ֽ������Ϊ���ֽڣ������ȡ���ֽ��������ܶࡣ

    Return value: a bytes object or ``None`` on timeout.

    ����ֵ��һ���ֽڶ����ʱʱ�ޡ�

    A bytes object contains a sequence of bytes. Because
    `ASCII <https://en.wikipedia.org/wiki/ASCII>`_ characters can fit in
    single bytes this type of object is often used to represent simple text
    and offers methods to manipulate it as such, e.g. you can display the text
    using the ``print()`` function.

    �ֽڶ������һϵ���ֽڡ���ΪASCII�ַ��ǵ����ֽڣ������������͵Ķ���ͨ�����ڱ�ʾ���ı������ṩ��Ӧ�Ĳ������������磬����ʹ��print����������ʾ�ı���

    You can also convert this object into a string object, and if there are
    non-ASCII characters present the encoding can be specified::

    �����Խ��˶���ת��Ϊ�ַ�������������ڷ�ASCII�ַ��������ָ�����룺

        msg_bytes = uart.read()
        msg_str = str(msg, 'UTF-8')

    .. note::

    ע�⣺

        The timeout for all UART reads depends on the baudrate and is otherwise
        not changeable via Python. The timeout, in milliseconds, is given by:

        ����UART��ȡ�ĳ�ʱȡ���ڲ����ʣ��಻��ͨ��python���ġ���ʱʱ�䣨�Ժ���Ϊ��
        λ�������¹�ʽ������

        ``microbit_uart_timeout_char = 13000 / baudrate + 1``

    .. note::

    ע�⣺

        The internal UART RX buffer is 64 bytes, so make sure data is read
        before the buffer is full or some of the data might be lost.

        �ڲ�UART RX������Ϊ64�ֽڣ������ȷ���ڻ�������֮ǰ��ȡ���ݣ�������ܻᶪʧĳЩ���ݡ�

    .. warning::

    ���棺

        Receiving ``0x03`` will stop your program by raising a Keyboard
        Interrupt. You can enable or disable this using
        :func:`micropython.kbd_intr()`.

        ����0x03�����������ж���ֹͣ���� ������ʹ�����û���ô˹��ܣ�micropython.kbd_intr()

.. method:: uart.readall()

    Removed since version 1.0.

    �Ӱ汾1.0��ȥ�˷�����

    Instead, use :func:`uart.read()` with no arguments, which will read as much data
    as possible.

    ���޲�uart.read()���������档�����Զ������ܶ�����ݡ�

.. method:: uart.readinto(buf[, nbytes])

   Read bytes into the ``buf``.  If ``nbytes`` is specified then read at most
   that many bytes.  Otherwise, read at most ``len(buf)`` bytes.

   ���ֽ�����������buf�С����ָ����nbytes�����ȡnbytesָ�����ֽ����������ȡ������buf��С���ֽ�����

   Return value: number of bytes read and stored into ``buf`` or ``None`` on
   timeout.

   ����ֵ������д�뻺����buf���ֽ���ֵ����ʱ�򷵻�None��

.. method:: uart.readline()

   Read a line, ending in a newline character.

   ��һ�У��Ի��з���β��

   Return value: the line read or ``None`` on timeout. The newline character is
   included in the returned bytes.

   ����ֵ����ȡ���У���ʱ����None�����з������ڷ��ص��ֽ��С�

.. method:: uart.write(buf)

    Write the buffer to the bus, it can be a bytes object or a string::

    д���������ݵ������ϣ����������ֽڶ�����ַ�����

        uart.write('hello world')
        uart.write(b'hello world')
        uart.write(bytes([1, 2, 3]))

    Return value: number of bytes written or ``None`` on timeout.

    ����ֵ��д����ֽ�������ʱ����None��
