SPI
***

.. py:module:: microbit.spi

The ``spi`` module lets you talk to a device connected to your board using
a serial peripheral interface (SPI) bus. SPI uses a so-called master-slave
architecture with a single master. You will need to specify the connections
for three signals:

spi模块允许与通过串行外设接口SPI连接到板上的设备通信。SPI使用所谓的单个主的主从结构。需要明确三种信号的连接：

* SCLK : Serial Clock (output from master).
* SCLK :串行时钟（主设备输出）
* MOSI : Master Output, Slave Input (output from master).
* MOSI :主设备输出，从设备输入（主设备输出）
* MISO : Master Input, Slave Output (output from slave).
* MISO :主设备输入，从设备输出（从设备输出）


Functions 函数
=========

.. method:: init(baudrate=1000000, bits=8, mode=0, sclk=pin13, mosi=pin15, miso=pin14)

    Initialize SPI communication with the specified parameters on the
    specified ``pins``. Note that for correct communication, the parameters
    have to be the same on both communicating devices.

    初始化指定引脚的SPI通信参数。注意，为了正确通信，两个设备的通信参数必须一致。

    The ``baudrate`` defines the speed of communication.

    baudrate定义通信速率。

    The ``bits`` defines the size of bytes being transmitted. Currently only
    ``bits=8`` is supported. However, this may change in the future.

    bits定义传输字节位数。现在只支持8位。不过将来可能会改变。

    The ``mode`` determines the combination of clock polarity and phase
    according to the following convention, with polarity as the high order bit
    and phase as the low order bit:

    mode根据以下约定确定时钟极性和相位的组合，极性为高阶位，相位为低阶位：

    +----------+-----------------+--------------+
    | SPI Mode | Polarity (CPOL) | Phase (CPHA) |
    +==========+=================+==============+
    | 0        | 0               | 0            |
    +----------+-----------------+--------------+
    | 1        | 0               | 1            |
    +----------+-----------------+--------------+
    | 2        | 1               | 0            |
    +----------+-----------------+--------------+
    | 3        | 1               | 1            |
    +----------+-----------------+--------------+

    Polarity (aka CPOL) 0 means that the clock is at logic value 0 when idle
    and goes high (logic value 1) when active; polarity 1 means the clock is
    at logic value 1 when idle and goes low (logic value 0) when active. Phase
    (aka CPHA) 0 means that data is sampled on the leading edge of the clock,
    and 1 means on the trailing edge
    (viz. https://en.wikipedia.org/wiki/Signal_edge).

    极性（也称为CPOL）0表示时钟在空闲时为逻辑值0，在活动时变为高（逻辑值1）；极性1表
    示时钟在空闲时为逻辑值1，在活动时变为低（逻辑值0）。相位（也称 CPHA）0表示在时钟
    的前沿对数据进行采样，1表示在后沿对数据进行采样（即https://en.wikipedia.org/
    wiki/signal_-edge）。

    The ``sclk``, ``mosi`` and ``miso`` arguments specify the pins to use for
    each type of signal.

    sclk、mosi、miso指定相应信号的引脚。

.. method:: spi.read(nbytes)

   Read at most ``nbytes``. Returns what was read.

   读取nbytes指定的数据长度。返回读取的数据。

.. method:: spi.write(buffer)

   Write the ``buffer`` of bytes to the bus.

   写buffer字节数据到总线上。

.. method:: spi.write_readinto(out, in)

   Write the ``out`` buffer to the bus and read any response into the ``in``
   buffer. The length of the buffers should be the same. The buffers can be
   the same object.

   写out缓冲区的数据到总线，并将任何响应读取到in缓冲区。缓冲区的长度应该相同。缓冲区可以是同一个类。
