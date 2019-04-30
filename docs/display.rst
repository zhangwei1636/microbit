Display 显示
*******

.. py:module:: microbit.display

This module controls the 5脳5 LED display on the front of your board. It can
be used to display images, animations and even text.

该模块控制电路板上面的5×5 LED显示屏。 它可用于显示图片、动画甚至文本。

.. image:: scroll-hello.gif

Functions
=========

.. py:function:: get_pixel(x, y)

    Return the brightness of the LED at column ``x`` and row ``y`` as an
    integer between 0 (off) and 9 (bright).

    返回x行y列的像素的亮度值，取值范围为0（关）- 9（最亮）整数。


.. py:function:: set_pixel(x, y, value)

    Set the brightness of the LED at column ``x`` and row ``y`` to ``value``,
    which has to be an integer between 0 and 9.

    设置x行y列像素的亮度值value，取值范围0-9的整数。


.. py:function:: clear()

    Set the brightness of all LEDs to 0 (off).

    设置LED亮度全为零。

.. py:function:: show(image)

    Display the ``image``.

    显示image。


.. py:function:: show(value, delay=400, \*, wait=True, loop=False, clear=False)

    If ``value`` is a string, float or integer, display letters/digits in sequence.
    Otherwise, if ``value`` is an iterable sequence of images, display these images in sequence.
    Each letter, digit or image is shown with ``delay`` milliseconds between them.

    如果value是字符串、浮点数或整型数，则按顺序显示字母/数字。 否则，如果value是可循环的图像序列，则按顺序显示这些图像。 每个字母、数字或图像之间显示都延迟delay毫秒。

    If ``wait`` is ``True``, this function will block until the animation is
    finished, otherwise the animation will happen in the background.

    如果wait为True，则此函数将阻塞，直到动画结束，否则动画将在后台进行。

    If ``loop`` is ``True``, the animation will repeat forever.

    如果loop是True，动画将一直重复。

    If ``clear`` is ``True``, the display will be cleared after the iterable has finished.

    如果clear是True，循环结束后将清除显示。

    Note that the ``wait``, ``loop`` and ``clear`` arguments must be specified
    using their keyword.

    注意，wait、loop和clear参数的值必须使用指定的关键字（True或False）。

.. note::

注意：
    If using a generator as the ``iterable``, then take care not to allocate any memory
    in the generator as allocating memory in an interrupt is prohibited and will raise a
    ``MemoryError``.

    如果使用生成器作为iterable，那么请注意不要给生成器分配任何内存，因为在中断中分配
    内存是禁止的，并会引发MemoryError错误。

.. py:function:: scroll(value, delay=150, \*, wait=True, loop=False, monospace=False)

    Scrolls ``value`` horizontally on the display. If ``value`` is an integer or float it is
    first converted to a string using ``str()``. The ``delay`` parameter controls how fast
    the text is scrolling.

    在显示器上水平滚动value值。如果value值是整数或浮点，则首先使用str（）将其转换为字符串。delay参数控制文本滚动的速度。

    If ``wait`` is ``True``, this function will block until the animation is
    finished, otherwise the animation will happen in the background.

    如果wait为true，则此函数将阻塞，直到动画完成，否则动画将在后台运行。

    If ``loop`` is ``True``, the animation will repeat forever.

    如果loop为True，动画将一直重复运行。

    If ``monospace`` is ``True``, the characters will all take up 5 pixel-columns
    in width, otherwise there will be exactly 1 blank pixel-column between each
    character as they scroll.

    如果monospace为True，字符宽度将全部占5个像素列，否则滚动时每个字符之间正好有1个空白像素列。

    Note that the ``wait``, ``loop`` and ``monospace`` arguments must be specified
    using their keyword.

    请注意，必须使用关键字（True或False）指定wait、loop和monospace参数。

.. py:function:: on()

    Use on() to turn on the display.

    使用on（）打开显示。

.. py:function:: off()

    Use off() to turn off the display (thus allowing you to re-use the GPIO
    pins associated with the display for other purposes).

    使用off（）关闭显示（从而允许重用与显示器关联的GPIO管脚）。

.. py:function:: is_on()

    Returns ``True`` if the display is on, otherwise returns ``False``.

    如果显示屏开则返回True，否则返回False.

.. py:function:: read_light_level()

    Use the display's LEDs in reverse-bias mode to sense the amount of light
    falling on the display.  Returns an integer between 0 and 255 representing
    the light level, with larger meaning more light.

    在反向偏压模式下，使用显示器的LED来感应显示器上的光量。返回一个介于0和255之间的整数，表示灯光亮度级别，其值越大，表示灯光越亮。

Example 例子
=======

To continuously scroll a string across the display, and do it in the background,
you can use::

要在显示屏上连续滚动字符串，并在后台执行，您可以使用：

    import microbit

    microbit.display.scroll('Hello!', wait=False, loop=True)
