Buttons
-------

So far we have created code that makes the device do something. This is called
*output*. However, we also need the device to react to things. Such things are
called *inputs*.

��ĿǰΪֹ�������Ѿ�������ʹ�豸�ܹ���ĳ�µĴ��롣 ���Ϊ����� ���ǣ����ǻ���
Ҫ�豸��������Ӧ�� �������鱻��Ϊ���롣

It's easy to remember: output is what the device puts out to the world
whereas input is what goes into the device for it to process.

�������׼�ס��������豸���ⷢ���Ķ������������ǽ����豸����������ݡ�

The most obvious means of input on the micro:bit are its two buttons, labelled
``A`` and ``B``. Somehow, we need MicroPython to react to button presses.

micro��bit�������Ե����뷽ʽ������������ť�����ΪA��B.���ԣ�������ҪMicroPython��
��Ӧ��ť���¡�

This is remarkably simple::
��ǳ��򵥣�

    from microbit import *

    sleep(10000)
    display.scroll(str(button_a.get_presses()))

All this script does is sleep for ten thousand milliseconds (i.e. 10 seconds)
and then scrolls the number of times you pressed button ``A``. That's it!
����ű�����ͣһ����루��10�룩��Ȼ������㰴�°�ťA�Ĵ���������������

While it's a pretty useless script, it introduces a couple of interesting new
ideas:
��Ȼ����һ���ǳ����õĽű�������������һЩ��Ȥ�����뷨��

#. The ``sleep`` *function* will make the micro:bit sleep for a certain number
   of milliseconds. If you want a pause in your program, this is how to do it.
   A *function* is just like a *method*, but it isn't attached by a dot to an
   *object*.
   ˯�ߺ�����ʹmicro:bit˯�߳���һ���ĺ������� ��������ڳ�������ͣһ�£��Ϳ���ʹ
   ����������� ��������һ����������������һ������ķ�����

#. There is an object called ``button_a`` and it allows you to get the number
   of times it has been pressed with the ``get_presses`` *method*.
   һ����button_a�Ķ�������������ȡʹ��get_presses����������ť���µĴ�����

Since ``get_presses`` gives a numeric value and ``display.scroll`` only
displays characters, we need to convert the numeric value into a string of
characters. We do this with the ``str`` function (short for "string" ~ it
converts things into strings of characters).
����get_presses����һ����ֵ����display.scrollֻ��ʾ�ַ���������Ҫ����ֵת��Ϊ��
������ ����ʹ��str����ִ�д˲�����str�ǡ�string������д��������������ת��Ϊ�ַ�������

The third line is a bit like an onion. If the parenthesis are the
onion skins then you'll notice that ``display.scroll`` contains ``str`` that
itself contains ``button_a.get_presses``. Python attempts to work out the
inner-most answer first before starting on the next layer out. This is called
*nesting* - the coding equivalent of a Russian Matrioshka doll.
�������е�����С� ������������Ƥ����ô���ע�⵽display.scroll����str������
str��������button_a.get_presses������ Python�����ڲ�������һ��һ��ִ�С� ���Ϊ
Ƕ�� - �����ڶ���˹Matrioshka��ߵı��롣

.. image:: matrioshka.jpg

Let's pretend you've pressed the button 10 times. Here's how Python works out
what's happening on the third line:
���Ǽ�װ�㰴��10�ΰ�ť�� ������Python��ν�������з��������飺

Python sees the complete line and gets the value of ``get_presses``::
Python����������һ�д�����get_presses��ֵ��

    display.scroll(str(button_a.get_presses()))

Now that Python knows how many button presses there have been, it converts the
numeric value into a string of characters::
��ȻPython֪����ť���¶��ٴΣ����ͽ�����ֵת��Ϊ�ַ���::

    display.scroll(str(10))

Finally, Python knows what to scroll across the display::
���Python֪������ʾ���Ϲ���������::

    display.scroll("10")

While this might seem like a lot of work, MicroPython makes this happen
extraordinarily fast.
��Ȼ����ܿ������ܶ๤������MicroPython���е÷ǳ��졣

Event Loops ���¼�ѭ����
+++++++++++

Often you need your program to hang around waiting for something to happen. To
do this you make it loop around a piece of code that defines how to react to
certain expected events such as a button press.
ͨ��������Ҫ�ȴ��¼������� Ϊ�ˣ�������ͨ��һ�δ���ѭ�����ô�����ĳ���¼����������簴�°�ť��

To make loops in Python you use the ``while`` keyword. It checks if something
is ``True``. If it is, it runs a *block of code* called the *body* of the loop.
If it isn't, it breaks out of the loop (ignoring the body) and the rest of the
program can continue.
Ҫ��Python�д���ѭ������ʹ��while�ؼ��֡� �����������Ƿ�ΪTrue�� ����ǣ��������г�Ϊѭ��
��Ĵ���顣 ������ǣ���������ѭ��������ѭ���壩������ִ�г�������ಿ�֡�

Python makes it easy to define blocks of code. Say I have a to-do list written
on a piece of paper. It probably looks something like this::
Python���Ժ����׵ض������顣 ����һ��ֽ��д�˴��������б� �����ܿ�������������

    Shopping
    Fix broken gutter
    Mow the lawn

If I wanted to break down my to-do list a bit further, I might write something
like this::
������һ��ϸ�ִ��������嵥�������б����£�

    Shopping:
        Eggs
        Bacon
        Tomatoes
    Fix broken gutter:
        Borrow ladder from next door
        Find hammer and nails
        Return ladder
    Mow the lawn:
        Check lawn around pond for frogs
        Check mower fuel level

It's obvious that the main tasks are broken down into sub-tasks that are
*indented* underneath the main task to which they are related. So ``Eggs``,
``Bacon`` and ``Tomatoes`` are obviously related to ``Shopping``. By indenting
things we make it easy to see, at a glance, how the tasks relate to each other.
�����ԣ���Ҫ���񱻷ֽ�Ϊ��������Щ����������������ص���Ҫ���������������С� ��
��Eggs��Bacon��Tomatoes��Ȼ��Shopping�йء� ͨ������������ǿ���һĿ��Ȼ�ؿ�����
������໥������

This is called *nesting*. We use nesting to define blocks of code like this::
���ΪǶ�ס� ����ʹ��Ƕ�����������飬������ʾ��

    from microbit import *

    while running_time() < 10000:
        display.show(Image.ASLEEP)

    display.show(Image.SURPRISED)

The ``running_time`` function returns the number of milliseconds since the
device started.
running_time���������豸������ĺ�������

The ``while running_time() < 10000:`` line checks if the running time is less
than 10000 milliseconds (i.e. 10 seconds). If it is, *and this is where we can
see scoping in action*, then it'll display ``Image.ASLEEP``. Notice how this is
indented underneath the ``while`` statement *just like in our to-do list*.
��while running_time����<10000�����д���������ʱ���Ƿ�С��10000���루��10�룩�� ����ǣ�
�������������ڣ���ô������ʾImage.ASLEEP�� ע�������while������������ģ����������ǵ�
���������б���һ����


Obviously, if the running time is equal to or greater than 10000 milliseconds
then the display will show ``Image.SURPRISED``. Why? Because the ``while``
condition will be False (``running_time`` is no longer ``< 10000``). In that
case the loop is finished and the program will continue after the ``while``
loop's block of code. It'll look like your device is asleep for 10
seconds before waking up with a surprised look on its face.
��Ȼ���������ʱ����ڻ����10000���룬����ʾ������ʾImage.SURPRISED�� Ϊʲô�� ��Ϊwhile
����ΪFalse��running_time����С��10000���� ����������£�ѭ��������������whileѭ�������
֮�����ִ�С� ����������豸˯��10���ӣ����ϴ��ž��ȵı���������

Try it!

Handling an Event �������¼���
+++++++++++++++++

If we want MicroPython to react to button press events we should put it into
an infinite loop and check if the button ``is_pressed``.
�������ϣ��MicroPython�԰�ť�����¼�������Ӧ������Ӧ�ý�����������ѭ���в���
�鰴ť�Ƿ񱻰��¡�

An infinite loop is easy::
����ѭ�������ף�

    while True:
        # Do stuff

(Remember, ``while`` checks if something is ``True`` to work out if it should
run its block of code. Since ``True`` is obviously ``True`` for all time, you
get an infinite loop!)
����ס��while��������Ƿ�Ϊ�棬��ȷ�����Ƿ�Ӧ�����������顣��Ϊ���桱��Ȼ��Զ��
����ģ��������õ�һ������ѭ������

Let's make a very simple cyber-pet. It's always sad unless you're pressing
button ``A``. If you press button ``B`` it dies. (I realise this isn't a very
pleasant game, so perhaps you can figure out how to improve it.)::
��������һ���ǳ��򵥵������� �����㰴�°�ťA�����������Ǻ��ѹ�������㰴�°�ťB��
���ͻ������� ������ʶ���ⲻ��һ���ǳ�������Ϸ������Ҳ���������취�Ľ���������

    from microbit import *

    while True:
        if button_a.is_pressed():
            display.show(Image.HAPPY)
        elif button_b.is_pressed():
            break
        else:
            display.show(Image.SAD)

    display.clear()

Can you see how we check what buttons are pressed? We used ``if``,
``elif`` (short for "else if") and ``else``. These are called *conditionals*
and work like this::
���ܿ���������μ�ⰴ�µİ�ť�� ����ʹ��if��elif����else if������д����else�� ��Щ����Ϊ������䣬������ʾ��

    if something is True:
        # do one thing
    elif some other thing is True:
        # do another thing
    else:
        # do yet another thing.

This is remarkably similar to English!
����Ӣ��ǳ����ƣ�

The ``is_pressed`` method only produces two results: ``True`` or ``False``.
If you're pressing the button it returns ``True``, otherwise it returns
``False``. The code above is saying, in English, "for ever and ever, if
button A is pressed then show a happy face, else if button B is pressed break
out of the loop, otherwise display a sad face." We break out of the loop (stop
the program running for ever and ever) with the ``break`` statement.
is_pressed����ֻ�������������True��False�� ��������°�ť������True�����򷵻�False��
����Ĵ�����˼�ǣ�����Զ����Զ��������°�ťAȻ����ʾһ�ſ��ֵ���������������°�ťB��
��ѭ����������ʾһ�ű��˵�����������ʹ��break�������ѭ������Զֹͣ�������У���

At the very end, when the cyber-pet is dead, we ``clear`` the display.
��󣬵�����������ˣ����������ʾ����

Can you think of ways to make this game less tragic? How would you check if
*both* buttons are pressed? (Hint: Python has ``and``, ``or`` and ``not``
logical operators to help check multiple truth statements (things that
produce either ``True`` or ``False`` results).
��������취�������Ϸ����ô������ ����μ��������ť�Ƿ񱻰��£� ����ʾ��Python
��AND��OR��NOT�߼�������������������ֵ��䣨����True��False�������䣩��

.. footer:: The image of Matrioshka dolls is licensed CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=69402
