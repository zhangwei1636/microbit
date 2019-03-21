Direction ������
---------

There is a compass on the BBC micro:bit. If you ever make a weather station
use the device to work out the wind direction.

BBC micro:bit����һ��ָ���롣����㽨�������վ��������ָ���������Է���

Compass ��ָ���룩
+++++++

It can also tell you the direction of North like this::

����ĳ���Ҳ���Ը����㱱���ķ���

    from microbit import *

    compass.calibrate()

    while True:
        needle = ((15 - compass.heading()) // 30) % 12
        display.show(Image.ALL_CLOCKS[needle])

.. note::
ע�⣺

    **You must calibrate the compass before taking readings.** Failure to do so
    will produce garbage results. The ``calibration`` method runs a fun little
    game to help the device work out where it is in relation to the Earth's
    magnetic field.

    �ڶ�ȡ����֮ǰ������У׼ָ���롣���򽫲������ý����calibration��������������һ����Ȥ��С��Ϸ�����������ָ���������ų��Ĺ�ϵ��

    To calibrate the compass, tilt the micro:bit around until a circle of pixels is
    drawn on the outside edges of the display.

    ҪУ׼ָ���룬�뽫micro:bitת��һȦ��ֱ������ʾ�������Ե����һ������Բ��

The program takes the ``compass.heading`` and, using some simple yet
cunning maths, `floor division <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_ ``//`` and `modulo <https://en.wikipedia.org/wiki/Modulo_operation>`_ ``%``, works out the number of the clock hand to use to display on the screen
so that it is pointing roughly North.

�ó������compass.heading����ʹ��һЩ�򵥶�������������ذ����//��ģ���������������
����Ļ����ʾ��ʱ��ָ������֣�ʹ�����ָ�򱱷���
