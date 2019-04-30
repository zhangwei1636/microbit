Buttons
*******

.. py::module:: microbit

There are two buttons on the board, called ``button_a`` and ``button_b``.

�����и���ť������button_a��button_b.

Attributes ����
==========


.. py:attribute:: button_a

    A ``Button`` instance (see below) representing the left button.

    Buttonʵ���������棩��ʾ��߰�����



.. py:attribute:: button_b

    Represents the right button.

    ��ʾ�ұ߰�����


Classes ��
=======

.. py:class:: Button()

    Represents a button.

    ��ʾһ��������

    .. note::

    ע�⣺
        This class is not actually available to the user, it is only used by
        the two button instances, which are provided already initialized.

        ����ʵ���϶��û������ã��������Ѿ���ʼ����������ťʵ��ʹ�á�


    .. py:method:: is_pressed()

        Returns ``True`` if the specified button ``button`` is currently being
        held down, and ``False`` otherwise.

        �����ǰ��סָ���İ�ť���򷵻ء��桱�����򷵻ء��١���

    .. py:method:: was_pressed()

        Returns ``True`` or ``False`` to indicate if the button was pressed
        (went from up to down) since the device started or the last time this
        method was called.  Calling this method will clear the press state so
        that the button must be pressed again before this method will return
        ``True`` again.

        ����True��False��ָʾ���豸�������ϴε��ô˷���ʱ��ť�Ƿ񱻰��£����ϵ��£���
        ���ô˷������������״̬���Ա��ڴ˷����ٴη���True֮ǰ�����ٴΰ��¸ð�ť��

    .. py:method:: get_presses()

        Returns the running total of button presses, and resets this total
        to zero before returning.

        ���ذ������������������ڷ���ǰ������������Ϊ�㡣

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
