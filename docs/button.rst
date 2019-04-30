Buttons
*******

.. py::module:: microbit

There are two buttons on the board, called ``button_a`` and ``button_b``.

板上有个按钮，叫做button_a和button_b.

Attributes 属性
==========


.. py:attribute:: button_a

    A ``Button`` instance (see below) representing the left button.

    Button实例（见下面）表示左边按键。



.. py:attribute:: button_b

    Represents the right button.

    表示右边按键。


Classes 类
=======

.. py:class:: Button()

    Represents a button.

    表示一个按键。

    .. note::

    注意：
        This class is not actually available to the user, it is only used by
        the two button instances, which are provided already initialized.

        该类实际上对用户不可用，它仅由已经初始化的两个按钮实例使用。


    .. py:method:: is_pressed()

        Returns ``True`` if the specified button ``button`` is currently being
        held down, and ``False`` otherwise.

        如果当前按住指定的按钮，则返回“真”，否则返回“假”。

    .. py:method:: was_pressed()

        Returns ``True`` or ``False`` to indicate if the button was pressed
        (went from up to down) since the device started or the last time this
        method was called.  Calling this method will clear the press state so
        that the button must be pressed again before this method will return
        ``True`` again.

        返回True或False以指示自设备启动或上次调用此方法时按钮是否被按下（从上到下）。
        调用此方法将清除按下状态，以便在此方法再次返回True之前必须再次按下该按钮。

    .. py:method:: get_presses()

        Returns the running total of button presses, and resets this total
        to zero before returning.

        返回按键的运行总数，并在返回前将此总数重置为零。

Example
=======

.. code::

    import microbit

    while True:
        if microbit.button_a.is_pressed() and microbit.button_b.is_pressed():
            microbit.display.scroll("AB")
            break
        elif microbit.button_a.is_pressed():
            microbit.display.scroll("A")
        elif microbit.button_b.is_pressed():
            microbit.display.scroll("B")
        microbit.sleep(100)
