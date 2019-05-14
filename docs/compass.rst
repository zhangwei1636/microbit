Compass 指南针
*******

.. py:module:: microbit.compass

This module lets you access the built-in electronic compass. Before using,
the compass should be calibrated, otherwise the readings may be wrong.

此模块允许您访问内置电子指南针。使用前应校准指南针，否则读数可能有误。

.. warning::

警告：

    Calibrating the compass will cause your program to pause until calibration
    is complete. Calibration consists of a little game to draw a circle on the
    LED display by rotating the device.

    校准指南针将导致程序暂停，直到校准完成。校准由通过旋转设备在LED显示屏上画一个圆的
    小程序组成。


Functions 函数
=========

.. py:function:: calibrate()

    Starts the calibration process. An instructive message will be scrolled
    to the user after which they will need to rotate the device in order to
    draw a circle on the LED display.

    开始校准过程。将向用户滚动显示一条指示信息，然后用户需要旋转设备，以便在LED显示
    屏上画一个圆圈。

.. py:function:: is_calibrated()

    Returns ``True`` if the compass has been successfully calibrated, and
    returns ``False`` otherwise.

    如果指南针校准成功则返回True，否则返回False。


.. py:function:: clear_calibration()

    Undoes the calibration, making the compass uncalibrated again.

    撤消校准，使指南针处于未校准。


.. py:function:: get_x()

    Gives the reading of the magnetic field strength on the ``x`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    根据磁场的方向，以正整数或负整数的形式给出x轴上磁场强度的读数，单位为纳特斯拉。


.. py:function:: get_y()

    Gives the reading of the magnetic field strength on the ``y`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    根据磁场的方向，以正整数或负整数的形式给出y轴上磁场强度的读数，单位为纳特斯拉。


.. py:function:: get_z()

    Gives the reading of the magnetic field strength on the ``z`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    根据磁场的方向，以正整数或负整数的形式给出z轴上磁场强度的读数，单位为纳特斯拉。


.. py:function:: heading()

    Gives the compass heading, calculated from the above readings, as an
    integer in the range from 0 to 360, representing the angle in degrees,
    clockwise, with north as 0.

    给出指南针方向，根据上述读数计算出的以0到360之间的整数表示的以度为单位的角度，
    顺时针为正，北为0度。


.. py:function:: get_field_strength()

    Returns an integer indication of the magnitude of the magnetic field around
    the device in nano tesla.

    返回设备周围磁场强度的整数值，单位为纳特斯拉。


Example 例子
=======

.. include:: ../examples/compass.py
    :code: python
