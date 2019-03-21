Hello, World!
-------------

The traditional way to start programming in a new language is to get your
computer to say, "Hello, World!".

学习新语言编程的传统方法是让你的计算机输出“Hello，World！”。

.. image:: ../scroll-hello.gif

This is easy with MicroPython::

使用MicroPython很容易：

    from microbit import *
    display.scroll("Hello, World!")

Each line does something special. The first line::

每一行都做一些特别的事。 第一行：

    from microbit import *

...tells MicroPython to get all the stuff it needs to work with the BBC
micro:bit. All this stuff is in a module called ``microbit`` (a module
is a library of pre-existing code). When you ``import`` something you're telling
MicroPython that you want to use it, and ``*`` is Python's way to say
*everything*. So, ``from microbit import *`` means, in English, "I want to be
able to use everything from the microbit code library".

...告诉MicroPython使用BBC micro：bit所需的所有代码。 所有这些代码都在一个名为
microbit的模块中（模块是一个预先存在的代码库）。 当导入你想要使用的代码时，Python
是用*表示“全部代码”。 因此，from microbit import *的意思是“我希望能够使用microbit
代码库中的所有代码”。

The second line::

第二行：

    display.scroll("Hello, World!")

...tells MicroPython to use the display to scroll the string of characters
"Hello, World!". The ``display`` part of that line is an *object* from the
``microbit`` module that represents the device's physical display (we say
"object" instead of "thingy", "whatsit" or "doodah"). We can tell the display
to do things with a full-stop ``.`` followed by what looks like a command (in
fact it's something we call a *method*). In this case we're using the
``scroll`` method. Since ``scroll`` needs to know what characters to scroll
across the physical display we specify them between double quotes (``"``)
within parenthesis (``(`` and ``)``). These are called the *arguments*. So,
``display.scroll("Hello, World!")`` means, in English, "I want you to use the
display to scroll the text 'Hello, World!'". If a method doesn't need any
arguments we make this clear by using empty parenthesis like this: ``()``.

...告诉MicroPython滚动显示字符串“Hello，World！”。 该行的显示部分是来自microbit
模块的对象，它代表设备的物理显示（我们说“对象”而不是“thingy”、“whatsit”或“doodah”）。
 我们用显示对象后加一点“.”来说明对象做什么事（实际上我们称之为方法）。 在这个例子，我们
使用的是“滚动”方法。 由于scroll需要知道在显示器中滚动显示哪些字符，我们在括号（）中的双引
号“”之间指定它们，这些称为参数。所以，display.scroll（“Hello，World！”）表示的意思
是“我希望你使用显示器来滚动显示文本‘Hello，World！’”。如果一个方法不需要任何参数，我们可以通
过使用空括号来清楚地说明这一点:(）。

Copy the "Hello, World!" code into your editor and flash it onto the device.
Can you work out how to change the message? Can you make it say hello to you?
For example, I might make it say "Hello, Nicholas!". Here's a clue, you need to
change the scroll method's argument.

将“Hello，World！”代码复制到编辑器中并将其刷新到设备上。 你能弄清楚如何改变信息吗？ 
你能让它跟你打招呼吗？ 例如，我想它说“你好，尼古拉斯！”。 提示一下，您需要更改scroll方法的参数。

.. warning::

.. 提醒::

    It may not work. :-)

    它可能无法正常工作

    This is where things get fun and MicroPython tries to be helpful. If
    it encounters an error it will scroll a helpful message on the micro:bit's
    display. If it can, it will tell you the line number for where the error
    can be found.
    
    这是事情变得有趣的地方，MicroPython试图提供帮助。 如果遇到错误，它将在micro：bit的显示屏上
    滚动一条帮助消息。 如果可能，它会告诉你出错的行号。

    Python expects you to type **EXACTLY** the right thing. So, for instance,
    ``Microbit``, ``microbit`` and ``microBit`` are all different things to
    Python. If MicroPython complains about a ``NameError`` it's probably
    because you've typed something inaccurately. It's like the difference
    between referring to "Nicholas" and "Nicolas". They're two different people
    but their names look very similar.

    Python要求输入精确。 因此，Microbit，microbit和microBit对于Python都是不同的。 如果MicroPython显
    示NameError错误，可能是因为你输入的内容不准确。 这就像提到“Nicholas”和“Nicolas”之间的区别。
    他们是两个不同的人，但他们的名字看起来很相似。

    If MicroPython complains about a ``SyntaxError`` you've simply typed code
    in a way that MicroPython can't understand. Check you're not missing any
    special characters like ``"`` or ``:``. It's like putting. a full stop in
    the middle of a sentence. It's hard to understand exactly what you mean.

    如果以MicroPython无法理解的方式键入代码，MicroPython就会显示SyntaxError错误。检查你有没有遗漏
    任何特殊字符，比如“或：等。就像把句号放在句子中间一样。就很难理解句子的意思了。

    Your microbit may stop responding: you cannot flash new code to it or
    enter commands into the REPL. If this happens, try power cycling it. That
    is, unplug the USB cable (and battery cable if it's connected), then plug
    the cable back in again. You may also need to quit and re-start your code
    editor application.

    您的microbit可能会停止响应：您无法向其中刷新代码或在REPL中输入命令。 如果发生这种情况，请尝试重启电源。
    也就是说，拔下USB电缆（如果已连接电池电缆，则拔掉电池电缆），然后重新插入电缆。 您可能还需要退出并重新
    启动代码编辑器。
