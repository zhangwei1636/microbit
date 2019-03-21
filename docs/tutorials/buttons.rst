Buttons
-------

So far we have created code that makes the device do something. This is called
*output*. However, we also need the device to react to things. Such things are
called *inputs*.

到目前为止，我们已经创建了使设备能够做某事的代码。 这称为输出。 但是，我们还需
要设备来做出反应。 这种事情被称为输入。

It's easy to remember: output is what the device puts out to the world
whereas input is what goes into the device for it to process.

它很容易记住：输出是设备向外发出的东西，而输入是进入设备被处理的内容。

The most obvious means of input on the micro:bit are its two buttons, labelled
``A`` and ``B``. Somehow, we need MicroPython to react to button presses.

micro：bit上最明显的输入方式是它的两个按钮，标记为A和B.所以，我们需要MicroPython来
响应按钮按下。

This is remarkably simple::
这非常简单：

    from microbit import *

    sleep(10000)
    display.scroll(str(button_a.get_presses()))

All this script does is sleep for ten thousand milliseconds (i.e. 10 seconds)
and then scrolls the number of times you pressed button ``A``. That's it!
这个脚本先暂停一万毫秒（即10秒），然后滚动你按下按钮A的次数。就是这样！

While it's a pretty useless script, it introduces a couple of interesting new
ideas:
虽然它是一个非常无用的脚本，但它引入了一些有趣的新想法：

#. The ``sleep`` *function* will make the micro:bit sleep for a certain number
   of milliseconds. If you want a pause in your program, this is how to do it.
   A *function* is just like a *method*, but it isn't attached by a dot to an
   *object*.
   睡眠函数将使micro:bit睡眠持续一定的毫秒数。 如果你想在程序中暂停一下，就可以使
   用这个函数。 函数就像一个方法，但它不是一个对象的方法。

#. There is an object called ``button_a`` and it allows you to get the number
   of times it has been pressed with the ``get_presses`` *method*.
   一个叫button_a的对象，它允许您获取使用get_presses方法计数按钮按下的次数。

Since ``get_presses`` gives a numeric value and ``display.scroll`` only
displays characters, we need to convert the numeric value into a string of
characters. We do this with the ``str`` function (short for "string" ~ it
converts things into strings of characters).
由于get_presses给出一个数值而且display.scroll只显示字符，我们需要将数值转换为字
符串。 我们使用str函数执行此操作（str是“string”的缩写，它将其他类型转换为字符串）。

The third line is a bit like an onion. If the parenthesis are the
onion skins then you'll notice that ``display.scroll`` contains ``str`` that
itself contains ``button_a.get_presses``. Python attempts to work out the
inner-most answer first before starting on the next layer out. This is called
*nesting* - the coding equivalent of a Russian Matrioshka doll.
第三行有点像洋葱。 如果括号是洋葱皮，那么你会注意到display.scroll包含str函数，
str函数包含button_a.get_presses参数。 Python从最内部向外面一层一层执行。 这称为
嵌套 - 类似于俄罗斯Matrioshka玩具的编码。

.. image:: matrioshka.jpg

Let's pretend you've pressed the button 10 times. Here's how Python works out
what's happening on the third line:
我们假装你按了10次按钮。 以下是Python如何解决第三行发生的事情：

Python sees the complete line and gets the value of ``get_presses``::
Python根据完整的一行代码获得get_presses的值：

    display.scroll(str(button_a.get_presses()))

Now that Python knows how many button presses there have been, it converts the
numeric value into a string of characters::
既然Python知道按钮按下多少次，它就将此数值转换为字符串::

    display.scroll(str(10))

Finally, Python knows what to scroll across the display::
最后，Python知道在显示屏上滚动的内容::

    display.scroll("10")

While this might seem like a lot of work, MicroPython makes this happen
extraordinarily fast.
虽然这可能看起来很多工作，但MicroPython运行得非常快。

Event Loops （事件循环）
+++++++++++

Often you need your program to hang around waiting for something to happen. To
do this you make it loop around a piece of code that defines how to react to
certain expected events such as a button press.
通常程序需要等待事件发生。 为此，您可以通过一段代码循环，该代码检测某个事件发生，例如按下按钮。

To make loops in Python you use the ``while`` keyword. It checks if something
is ``True``. If it is, it runs a *block of code* called the *body* of the loop.
If it isn't, it breaks out of the loop (ignoring the body) and the rest of the
program can continue.
要在Python中创建循环，请使用while关键字。 它会检查条件是否为True。 如果是，它会运行称为循环
体的代码块。 如果不是，它会跳出循环（忽略循环体），继续执行程序的其余部分。

Python makes it easy to define blocks of code. Say I have a to-do list written
on a piece of paper. It probably looks something like this::
Python可以很容易地定义代码块。 如在一张纸上写了待办事项列表。 它可能看起来像这样：

    Shopping
    Fix broken gutter
    Mow the lawn

If I wanted to break down my to-do list a bit further, I might write something
like this::
如果想进一步细分待办事项清单，可能列表如下：

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
很明显，主要任务被分解为子任务，这些子任务在与它们相关的主要任务下面缩进排列。 所
以Eggs，Bacon和Tomatoes显然与Shopping有关。 通过缩进事物，我们可以一目了然地看到任
务如何相互关联。

This is called *nesting*. We use nesting to define blocks of code like this::
这称为嵌套。 我们使用嵌套来定义代码块，如下所示：

    from microbit import *

    while running_time() < 10000:
        display.show(Image.ASLEEP)

    display.show(Image.SURPRISED)

The ``running_time`` function returns the number of milliseconds since the
device started.
running_time函数返回设备启动后的毫秒数。

The ``while running_time() < 10000:`` line checks if the running time is less
than 10000 milliseconds (i.e. 10 seconds). If it is, *and this is where we can
see scoping in action*, then it'll display ``Image.ASLEEP``. Notice how this is
indented underneath the ``while`` statement *just like in our to-do list*.
“while running_time（）<10000”这行代码检查运行时间是否小于10000毫秒（即10秒）。 如果是，
并且在作用域内，那么它将显示Image.ASLEEP。 注意如何在while语句下面缩进的，就像在我们的
待办事项列表中一样。


Obviously, if the running time is equal to or greater than 10000 milliseconds
then the display will show ``Image.SURPRISED``. Why? Because the ``while``
condition will be False (``running_time`` is no longer ``< 10000``). In that
case the loop is finished and the program will continue after the ``while``
loop's block of code. It'll look like your device is asleep for 10
seconds before waking up with a surprised look on its face.
显然，如果运行时间等于或大于10000毫秒，则显示器将显示Image.SURPRISED。 为什么？ 因为while
条件为False（running_time不再小于10000）。 在这种情况下，循环结束，程序将在while循环代码块
之后继续执行。 看起来你的设备睡了10秒钟，脸上带着惊讶的表情醒来。

Try it!

Handling an Event （处理事件）
+++++++++++++++++

If we want MicroPython to react to button press events we should put it into
an infinite loop and check if the button ``is_pressed``.
如果我们希望MicroPython对按钮按下事件作出反应，我们应该将其置于无限循环中并检
查按钮是否被按下。

An infinite loop is easy::
无限循环很容易：

    while True:
        # Do stuff

(Remember, ``while`` checks if something is ``True`` to work out if it should
run its block of code. Since ``True`` is obviously ``True`` for all time, you
get an infinite loop!)
（记住，while检查条件是否为真，以确定它是否应该运行其代码块。因为“真”显然永远都
是真的，所以你会得到一个无限循环！）

Let's make a very simple cyber-pet. It's always sad unless you're pressing
button ``A``. If you press button ``B`` it dies. (I realise this isn't a very
pleasant game, so perhaps you can figure out how to improve it.)::
让我们做一个非常简单的网络宠物。 除非你按下按钮A，否则它总是很难过。如果你按下按钮B，
它就会死掉。 （我意识到这不是一个非常愉快的游戏，所以也许你可以想办法改进它。）：

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
你能看到我们如何检测按下的按钮吗？ 我们使用if、elif（“else if”的缩写）和else。 这些被称为条件语句，如下所示：

    if something is True:
        # do one thing
    elif some other thing is True:
        # do another thing
    else:
        # do yet another thing.

This is remarkably similar to English!
这与英语非常相似！

The ``is_pressed`` method only produces two results: ``True`` or ``False``.
If you're pressing the button it returns ``True``, otherwise it returns
``False``. The code above is saying, in English, "for ever and ever, if
button A is pressed then show a happy face, else if button B is pressed break
out of the loop, otherwise display a sad face." We break out of the loop (stop
the program running for ever and ever) with the ``break`` statement.
is_pressed方法只产生两个结果：True或False。 如果您按下按钮，返回True，否则返回False。
上面的代码意思是：“永远，永远，如果按下按钮A然后显示一张快乐的脸，否则如果按下按钮B跳
出循环，否则显示一张悲伤的脸。”我们使用break语句跳出循环（永远停止程序运行）。

At the very end, when the cyber-pet is dead, we ``clear`` the display.
最后，当网络宠物死了，我们清除显示屏。

Can you think of ways to make this game less tragic? How would you check if
*both* buttons are pressed? (Hint: Python has ``and``, ``or`` and ``not``
logical operators to help check multiple truth statements (things that
produce either ``True`` or ``False`` results).
你能想出办法让这个游戏不那么悲惨吗？ 你如何检查两个按钮是否被按下？ （提示：Python
有AND、OR和NOT逻辑运算符来帮助检查多个真值语句（产生True或False结果的语句）。

.. footer:: The image of Matrioshka dolls is licensed CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=69402
