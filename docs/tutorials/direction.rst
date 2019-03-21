Direction （方向）
---------

There is a compass on the BBC micro:bit. If you ever make a weather station
use the device to work out the wind direction.

BBC micro:bit上有一个指南针。如果你建设过气象站，就是用指南针来测试风向。

Compass （指南针）
+++++++

It can also tell you the direction of North like this::

下面的程序也可以告诉你北方的方向：

    from microbit import *

    compass.calibrate()

    while True:
        needle = ((15 - compass.heading()) // 30) % 12
        display.show(Image.ALL_CLOCKS[needle])

.. note::
注意：

    **You must calibrate the compass before taking readings.** Failure to do so
    will produce garbage results. The ``calibration`` method runs a fun little
    game to help the device work out where it is in relation to the Earth's
    magnetic field.

    在读取读数之前，必须校准指南针。否则将产生无用结果。calibration（）方法运行了一个有趣的小游戏，帮助计算出指南针与地球磁场的关系。

    To calibrate the compass, tilt the micro:bit around until a circle of pixels is
    drawn on the outside edges of the display.

    要校准指南针，请将micro:bit转动一圈，直到在显示屏的外边缘绘制一个像素圆。

The program takes the ``compass.heading`` and, using some simple yet
cunning maths, `floor division <https://en.wikipedia.org/wiki/Floor_and_ceiling_functions>`_ ``//`` and `modulo <https://en.wikipedia.org/wiki/Modulo_operation>`_ ``%``, works out the number of the clock hand to use to display on the screen
so that it is pointing roughly North.

该程序采用compass.heading，并使用一些简单而巧妙的算术（地板除法//和模数％）计算出用于
在屏幕上显示的时钟指针的数字，使其大致指向北方。
