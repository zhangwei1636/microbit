SPI
***

.. py:module:: microbit.spi

The ``spi`` module lets you talk to a device connected to your board using
a serial peripheral interface (SPI) bus. SPI uses a so-called master-slave
architecture with a single master. You will need to specify the connections
for three signals:

spiģ��������ͨ����������ӿ�SPI���ӵ����ϵ��豸ͨ�š�SPIʹ����ν�ĵ����������ӽṹ����Ҫ��ȷ�����źŵ����ӣ�

* SCLK : Serial Clock (output from master).
* SCLK :����ʱ�ӣ����豸�����
* MOSI : Master Output, Slave Input (output from master).
* MOSI :���豸��������豸���루���豸�����
* MISO : Master Input, Slave Output (output from slave).
* MISO :���豸���룬���豸��������豸�����


Functions ����
=========

.. method:: init(baudrate=1000000, bits=8, mode=0, sclk=pin13, mosi=pin15, miso=pin14)

    Initialize SPI communication with the specified parameters on the
    specified ``pins``. Note that for correct communication, the parameters
    have to be the same on both communicating devices.

    ��ʼ��ָ�����ŵ�SPIͨ�Ų�����ע�⣬Ϊ����ȷͨ�ţ������豸��ͨ�Ų�������һ�¡�

    The ``baudrate`` defines the speed of communication.

    baudrate����ͨ�����ʡ�

    The ``bits`` defines the size of bytes being transmitted. Currently only
    ``bits=8`` is supported. However, this may change in the future.

    bits���崫���ֽ�λ��������ֻ֧��8λ�������������ܻ�ı䡣

    The ``mode`` determines the combination of clock polarity and phase
    according to the following convention, with polarity as the high order bit
    and phase as the low order bit:

    mode��������Լ��ȷ��ʱ�Ӽ��Ժ���λ����ϣ�����Ϊ�߽�λ����λΪ�ͽ�λ��

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

    ���ԣ�Ҳ��ΪCPOL��0��ʾʱ���ڿ���ʱΪ�߼�ֵ0���ڻʱ��Ϊ�ߣ��߼�ֵ1��������1��
    ʾʱ���ڿ���ʱΪ�߼�ֵ1���ڻʱ��Ϊ�ͣ��߼�ֵ0������λ��Ҳ�� CPHA��0��ʾ��ʱ��
    ��ǰ�ض����ݽ��в�����1��ʾ�ں��ض����ݽ��в�������https://en.wikipedia.org/
    wiki/signal_-edge����

    The ``sclk``, ``mosi`` and ``miso`` arguments specify the pins to use for
    each type of signal.

    sclk��mosi��misoָ����Ӧ�źŵ����š�

.. method:: spi.read(nbytes)

   Read at most ``nbytes``. Returns what was read.

   ��ȡnbytesָ�������ݳ��ȡ����ض�ȡ�����ݡ�

.. method:: spi.write(buffer)

   Write the ``buffer`` of bytes to the bus.

   дbuffer�ֽ����ݵ������ϡ�

.. method:: spi.write_readinto(out, in)

   Write the ``out`` buffer to the bus and read any response into the ``in``
   buffer. The length of the buffers should be the same. The buffers can be
   the same object.

   дout�����������ݵ����ߣ������κ���Ӧ��ȡ��in���������������ĳ���Ӧ����ͬ��������������ͬһ���ࡣ
