Microbit Module Microbit ģ��
***************

.. py:module:: microbit


The ``microbit`` module gives you access to all the hardware that is built-in
into your board.

Microbitģ�����������������ڰ��е�����Ӳ����


Functions
=========

.. py:function:: panic(n)

    Enter a panic mode. Requires restart. Pass in an arbitrary integer <= 255
    to indicate a status::

    �������ģʽ����Ҫ������������������С��255��������ָʾ״̬��

        microbit.panic(255)


.. py:function:: reset()

    Restart the board.

    ������·�塣


.. py:function:: sleep(n)

    Wait for ``n`` milliseconds. One second is 1000 milliseconds, so::

    �ȴ�n΢�롣1�����1000΢�룬���£�

        microbit.sleep(1000)

    will pause the execution for one second.  ``n`` can be an integer or
    a floating point number.

    ����ͣ1�롣n�������������߸�������


.. py:function:: running_time()

    Return the number of milliseconds since the board was switched on or
    restarted.

    ���ذ����ϵ���������ʱ�䡣


.. py:function:: temperature()

    Return the temperature of the micro:bit in degrees Celcius.

    ����microbit����¶ȶ�����


Attributes ����
==========

.. toctree::
    :maxdepth: 1

    button.rst
    pin.rst


Classes ��
=======

.. toctree::
    :maxdepth: 1

    image.rst


Modules ģ��
=======

.. toctree::
    :maxdepth: 1

    display.rst
    uart.rst
    spi.rst
    i2c.rst
    accelerometer.rst
    compass.rst
