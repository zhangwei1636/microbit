I²C
***

.. py:module:: microbit.i2c

The ``i2c`` module lets you communicate with devices connected to your board
using the I²C bus protocol. There can be multiple slave devices connected at
the same time, and each one has its own unique address, that is either fixed
for the device or configured on it. Your board acts as the I²C master.

I2Cģ��������ʹ��I2C����Э�����Ӱ���豸ͨ�š���ͬʱ���ԽӶ�����豸��ÿ���豸������
Ψһ�ĵ�ַ���������豸�̶��ĵ�ַ�������õĵ�ַ����İ���ΪI2C���豸��

We use 7-bit addressing for devices because of the reasons stated

������7λ�豸��ַ����Ϊ���ԭ��

`here <http://www.totalphase.com/support/articles/200349176-7-bit-8-bit-and-10-bit-I2C-Slave-Addressing>`_.

This may be different to other micro:bit related solutions.

��������micro:bit����صĽ��������ͬ��

How exactly you should communicate with the devices, that is, what bytes to
send and how to interpret the responses, depends on the device in question and
should be described separately in that device's documentation.

������ȷ���豸ͨ�ţ����Ͷ����ֽ����ݡ�����������Ӧ��ȡ��������豸�����豸�ĵ����е�����������


Functions ����
=========

.. py:function:: init(freq=100000, sda=pin20, scl=pin19)

    Re-initialize peripheral with the specified clock frequency ``freq`` on the
    specified ``sda`` and ``scl`` pins.

    ��ָ����sda��scl������ָ����ʱ��Ƶ��freq���³�ʼ�����衣

    .. warning::

    ���棺

        Changing the I²C pins from defaults will make the accelerometer and
        compass stop working, as they are connected internally to those pins.

        ����I2C���ŵ�Ĭ�����û�ʹ���ٶȼƺ�ָ����ֹͣ��������Ϊ�����ڲ�Ĭ�����ӵ����������š�


.. py:function:: scan()

    Scan the bus for devices.  Returns a list of 7-bit addresses corresponding
    to those devices that responded to the scan.

    ɨ�������豸���������豸��ص�7λ��ַ�б�


.. py:function:: read(addr, n, repeat=False)

    Read ``n`` bytes from the device with 7-bit address ``addr``. If ``repeat``
    is ``True``, no stop bit will be sent.

    ��7λ��ַaddr���豸�϶�ȡn���ֽ����ݡ����repeat��True���򲻷���ֹͣλ��


.. py:function:: write(addr, buf, repeat=False)

    Write bytes from ``buf`` to the device with 7-bit address ``addr``. If
    ``repeat`` is ``True``, no stop bit will be sent.

    ��buf������д�ֽڵ�7λ��ַΪaddr���豸�����repeat��True���򲻷���ֹͣλ��


Connecting ����
----------

You should connect the device's ``SCL`` pin to micro:bit pin 19, and the
device's ``SDA`` pin to micro:bit pin 20. You also must connect the device's
ground to the micro:bit ground (pin ``GND``). You may need to power the device
using an external power supply or the micro:bit.

�����豸��SCL���ŵ�micro:bit����19�������豸��SDA���ŵ�micro:bit����20.Ҳ���������豸�ĵص�micro:bit�ĵأ�GND���ţ�����������ⲿ��Դ��micro:bit���豸���硣

There are internal pull-up resistors on the I²C lines of the board, but with
particularly long wires or large number of devices you may need to add
additional pull-up resistors, to ensure noise-free communication.

���ϵ�I2C�����ڲ��������裬���ǵ���·�ر𳤻��߽����豸��ʱ��Ҫ����������裬��ʹͨ����������
