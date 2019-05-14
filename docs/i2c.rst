I虏C
***

.. py:module:: microbit.i2c

The ``i2c`` module lets you communicate with devices connected to your board
using the I虏C bus protocol. There can be multiple slave devices connected at
the same time, and each one has its own unique address, that is either fixed
for the device or configured on it. Your board acts as the I虏C master.

I2C模块允许与使用I2C总线协议连接板的设备通信。它同时可以接多个从设备，每个设备都有其
唯一的地址，可以是设备固定的地址或者配置的地址。你的板作为I2C主设备。

We use 7-bit addressing for devices because of the reasons stated

我们用7位设备地址是因为这个原因

`here <http://www.totalphase.com/support/articles/200349176-7-bit-8-bit-and-10-bit-I2C-Slave-Addressing>`_.

This may be different to other micro:bit related solutions.

这与其它micro:bit板相关的解决方案不同。

How exactly you should communicate with the devices, that is, what bytes to
send and how to interpret the responses, depends on the device in question and
should be described separately in that device's documentation.

怎样正确与设备通信，传送多少字节数据、怎样解释响应，取决于相关设备。在设备文档中有单独的描述。


Functions 函数
=========

.. py:function:: init(freq=100000, sda=pin20, scl=pin19)

    Re-initialize peripheral with the specified clock frequency ``freq`` on the
    specified ``sda`` and ``scl`` pins.

    在指定的sda和scl引脚用指定的时钟频率freq重新初始化外设。

    .. warning::

    警告：

        Changing the I虏C pins from defaults will make the accelerometer and
        compass stop working, as they are connected internally to those pins.

        更改I2C引脚的默认设置会使加速度计和指南针停止工作。因为它们内部默认连接到这两个引脚。


.. py:function:: scan()

    Scan the bus for devices.  Returns a list of 7-bit addresses corresponding
    to those devices that responded to the scan.

    扫描总线设备。返回与设备相关的7位地址列表。


.. py:function:: read(addr, n, repeat=False)

    Read ``n`` bytes from the device with 7-bit address ``addr``. If ``repeat``
    is ``True``, no stop bit will be sent.

    从7位地址addr的设备上读取n个字节数据。如果repeat是True，则不发送停止位。


.. py:function:: write(addr, buf, repeat=False)

    Write bytes from ``buf`` to the device with 7-bit address ``addr``. If
    ``repeat`` is ``True``, no stop bit will be sent.

    从buf缓冲区写字节到7位地址为addr的设备。如果repeat是True，则不发送停止位。


Connecting 连接
----------

You should connect the device's ``SCL`` pin to micro:bit pin 19, and the
device's ``SDA`` pin to micro:bit pin 20. You also must connect the device's
ground to the micro:bit ground (pin ``GND``). You may need to power the device
using an external power supply or the micro:bit.

连接设备的SCL引脚到micro:bit引脚19，连接设备的SDA引脚到micro:bit引脚20.也必须连接设备的地到micro:bit的地（GND引脚）。你必须用外部电源或micro:bit给设备供电。

There are internal pull-up resistors on the I虏C lines of the board, but with
particularly long wires or large number of devices you may need to add
additional pull-up resistors, to ensure noise-free communication.

板上的I2C线有内部上拉电阻，但是当线路特别长或者接入设备多时需要外加上拉电阻，以使通信无噪声。
