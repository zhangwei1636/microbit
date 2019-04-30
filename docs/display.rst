Display ��ʾ
*******

.. py:module:: microbit.display

This module controls the 5×5 LED display on the front of your board. It can
be used to display images, animations and even text.

��ģ����Ƶ�·�������5��5 LED��ʾ���� ����������ʾͼƬ�����������ı���

.. image:: scroll-hello.gif

Functions
=========

.. py:function:: get_pixel(x, y)

    Return the brightness of the LED at column ``x`` and row ``y`` as an
    integer between 0 (off) and 9 (bright).

    ����x��y�е����ص�����ֵ��ȡֵ��ΧΪ0���أ�- 9��������������


.. py:function:: set_pixel(x, y, value)

    Set the brightness of the LED at column ``x`` and row ``y`` to ``value``,
    which has to be an integer between 0 and 9.

    ����x��y�����ص�����ֵvalue��ȡֵ��Χ0-9��������


.. py:function:: clear()

    Set the brightness of all LEDs to 0 (off).

    ����LED����ȫΪ�㡣

.. py:function:: show(image)

    Display the ``image``.

    ��ʾimage��


.. py:function:: show(value, delay=400, \*, wait=True, loop=False, clear=False)

    If ``value`` is a string, float or integer, display letters/digits in sequence.
    Otherwise, if ``value`` is an iterable sequence of images, display these images in sequence.
    Each letter, digit or image is shown with ``delay`` milliseconds between them.

    ���value���ַ�����������������������˳����ʾ��ĸ/���֡� �������value�ǿ�ѭ����ͼ�����У���˳����ʾ��Щͼ�� ÿ����ĸ�����ֻ�ͼ��֮����ʾ���ӳ�delay���롣

    If ``wait`` is ``True``, this function will block until the animation is
    finished, otherwise the animation will happen in the background.

    ���waitΪTrue����˺�����������ֱ���������������򶯻����ں�̨���С�

    If ``loop`` is ``True``, the animation will repeat forever.

    ���loop��True��������һֱ�ظ���

    If ``clear`` is ``True``, the display will be cleared after the iterable has finished.

    ���clear��True��ѭ�������������ʾ��

    Note that the ``wait``, ``loop`` and ``clear`` arguments must be specified
    using their keyword.

    ע�⣬wait��loop��clear������ֵ����ʹ��ָ���Ĺؼ��֣�True��False����

.. note::

ע�⣺
    If using a generator as the ``iterable``, then take care not to allocate any memory
    in the generator as allocating memory in an interrupt is prohibited and will raise a
    ``MemoryError``.

    ���ʹ����������Ϊiterable����ô��ע�ⲻҪ�������������κ��ڴ棬��Ϊ���ж��з���
    �ڴ��ǽ�ֹ�ģ���������MemoryError����

.. py:function:: scroll(value, delay=150, \*, wait=True, loop=False, monospace=False)

    Scrolls ``value`` horizontally on the display. If ``value`` is an integer or float it is
    first converted to a string using ``str()``. The ``delay`` parameter controls how fast
    the text is scrolling.

    ����ʾ����ˮƽ����valueֵ�����valueֵ�������򸡵㣬������ʹ��str��������ת��Ϊ�ַ�����delay���������ı��������ٶȡ�

    If ``wait`` is ``True``, this function will block until the animation is
    finished, otherwise the animation will happen in the background.

    ���waitΪtrue����˺�����������ֱ��������ɣ����򶯻����ں�̨���С�

    If ``loop`` is ``True``, the animation will repeat forever.

    ���loopΪTrue��������һֱ�ظ����С�

    If ``monospace`` is ``True``, the characters will all take up 5 pixel-columns
    in width, otherwise there will be exactly 1 blank pixel-column between each
    character as they scroll.

    ���monospaceΪTrue���ַ���Ƚ�ȫ��ռ5�������У��������ʱÿ���ַ�֮��������1���հ������С�

    Note that the ``wait``, ``loop`` and ``monospace`` arguments must be specified
    using their keyword.

    ��ע�⣬����ʹ�ùؼ��֣�True��False��ָ��wait��loop��monospace������

.. py:function:: on()

    Use on() to turn on the display.

    ʹ��on��������ʾ��

.. py:function:: off()

    Use off() to turn off the display (thus allowing you to re-use the GPIO
    pins associated with the display for other purposes).

    ʹ��off�����ر���ʾ���Ӷ�������������ʾ��������GPIO�ܽţ���

.. py:function:: is_on()

    Returns ``True`` if the display is on, otherwise returns ``False``.

    �����ʾ�����򷵻�True�����򷵻�False.

.. py:function:: read_light_level()

    Use the display's LEDs in reverse-bias mode to sense the amount of light
    falling on the display.  Returns an integer between 0 and 255 representing
    the light level, with larger meaning more light.

    �ڷ���ƫѹģʽ�£�ʹ����ʾ����LED����Ӧ��ʾ���ϵĹ���������һ������0��255֮�����������ʾ�ƹ����ȼ�����ֵԽ�󣬱�ʾ�ƹ�Խ����

Example ����
=======

To continuously scroll a string across the display, and do it in the background,
you can use::

Ҫ����ʾ�������������ַ��������ں�ִ̨�У�������ʹ�ã�

    import microbit

    microbit.display.scroll('Hello!', wait=False, loop=True)
