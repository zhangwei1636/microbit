Accelerometer
*************

.. py:module:: microbit.accelerometer

This object gives you access to the on-board accelerometer. The accelerometer
also provides convenience functions for detecting gestures. The
recognised gestures are: ``up``, ``down``, ``left``, ``right``, ``face up``,
``face down``, ``freefall``, ``3g``, ``6g``, ``8g``, ``shake``.

这个对象让你访问板上的加速度计。加速度计还提供了便利的函数检测手势。可识别的手势有：``up``, ``down``, ``left``, ``right``, ``face up``,
``face down``, ``freefall``, ``3g``, ``6g``, ``8g``, ``shake``.

By default MicroPython sets the accelerometer range to +/- 2g, changing the
accelerometer range is currently not possible in MicroPython.
The accelerometer returns a value in the range 0..1024 for each axis, which is
then scaled accordingly.

默认情况下，Micropython将加速度计范围设置为+/-2g，目前无法在Micropython中更改加速度计范围。加速度计为每个轴返回一个0到1024范围内的值，然后相应地缩放该值。



Functions 函数
=========

.. py:function:: get_x()

    Get the acceleration measurement in the ``x`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    根据方向，以正整数或负整数的形式获取x轴上的加速度测量值。测量值以mg为单位。默认
    情况下，加速度计的配置范围为+/-2g，因此该方法将返回到+/-2000mg的范围内。

.. py:function:: get_y()

    Get the acceleration measurement in the ``y`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    根据方向，以正整数或负整数的形式获取y轴上的加速度测量值。测量值以mg为单位。默认
    情况下，加速度计的配置范围为+/-2g，因此该方法将返回到+/-2000mg的范围内。

.. py:function:: get_z()

    Get the acceleration measurement in the ``z`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    根据方向，以正整数或负整数的形式获取z轴上的加速度测量值。测量值以mg为单位。默认
    情况下，加速度计的配置范围为+/-2g，因此该方法将返回到+/-2000mg的范围内。

.. py:function:: get_values()

    Get the acceleration measurements in all axes at once, as a three-element
    tuple of integers ordered as X, Y, Z.
    By default the accelerometer is configured with a range of +/- 2g, and so
    X, Y, and Z will be within the range of +/-2000mg.

    一次获取所有轴上的加速度测量值，作为一个三元素整数数组，元素顺序为x、y、z。默认
    情况下，加速度计的配置范围为+/-2g，因此x、y和z将在+/-2000mg范围内取值。

.. py:function:: current_gesture()

    Return the name of the current gesture.

    返回当前手势的名称。

.. note::
注意：

    MicroPython understands the following gesture names: ``"up"``, ``"down"``,
    ``"left"``, ``"right"``, ``"face up"``, ``"face down"``, ``"freefall"``,
    ``"3g"``, ``"6g"``, ``"8g"``, ``"shake"``. Gestures are always
    represented as strings.

  Micropython识别以下手势名称：“向上”、“向下”、“左”、“右”、“面朝上”、“面朝下”、“自由落体”、“3g”、“6g”、“8g”、“震动”。手势总是用字符串表示。

.. py:function:: is_gesture(name)

    Return True or False to indicate if the named gesture is currently active.

    返回True或False，表示当前命名的手势是否激活。

.. py:function:: was_gesture(name)

    Return True or False to indicate if the named gesture was active since the
    last call.

    返回True或False以表示自上次调用以来命名手势是否处于活动状态。

.. py:function:: get_gestures()

    Return a tuple of the gesture history. The most recent is listed last.
    Also clears the gesture history before returning.

    返回手势历史的数组。最近的列在最后。并且在返回前清除手势历史记录。

.. note::

注意：

    Gestures are not updated in the background so there needs to be constant
    calls to some accelerometer method to do the gesture detection. Usually
    gestures can be detected using a loop with a small :func:`microbit.sleep` delay.

    手势不会在后台更新，因此需要不断调用某些加速度计方法来进行手势检测。通常，手势
    可以通过microbit.sleep（）延迟较短的循环来检测。

Examples 例子
--------

A fortune telling magic 8-ball. Ask a question then shake the device for an
answer.

算命魔术8球。 提出问题然后摇动设备以获得答案。

.. include:: ../examples/magic8.py
    :code: python

Simple Slalom. Move the device to avoid the obstacles.

简单的障碍赛，移动设备避开障碍物。

.. include:: ../examples/simple_slalom.py
    :code: python
