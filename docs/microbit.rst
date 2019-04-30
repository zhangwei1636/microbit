Microbit Module Microbit 模块
***************

.. py:module:: microbit


The ``microbit`` module gives you access to all the hardware that is built-in
into your board.

Microbit模块允许您访问内置在板中的所有硬件。


Functions
=========

.. py:function:: panic(n)

    Enter a panic mode. Requires restart. Pass in an arbitrary integer <= 255
    to indicate a status::

    进入紧急模式。需要重新启动。传入任意小于255的整数以指示状态：

        microbit.panic(255)


.. py:function:: reset()

    Restart the board.

    重启电路板。


.. py:function:: sleep(n)

    Wait for ``n`` milliseconds. One second is 1000 milliseconds, so::

    等待n微秒。1秒等于1000微秒，如下：

        microbit.sleep(1000)

    will pause the execution for one second.  ``n`` can be an integer or
    a floating point number.

    将暂停1秒。n可以是整数或者浮点数。


.. py:function:: running_time()

    Return the number of milliseconds since the board was switched on or
    restarted.

    返回板子上电或重启后的时间。


.. py:function:: temperature()

    Return the temperature of the micro:bit in degrees Celcius.

    返回microbit板的温度度数。


Attributes 属性
==========

.. toctree::
    :maxdepth: 1

    button.rst
    pin.rst


Classes 类
=======

.. toctree::
    :maxdepth: 1

    image.rst


Modules 模块
=======

.. toctree::
    :maxdepth: 1

    display.rst
    uart.rst
    spi.rst
    i2c.rst
    accelerometer.rst
    compass.rst
