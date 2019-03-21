Random
------

Sometimes you want to leave things to chance, or mix it up a little: you want
the device to act randomly.

有时你想让事情有机会发生，或者你想让设备随机动作。

MicroPython comes with a ``random`` module to make it easy to introduce chance
and a little chaos into your code. For example, here's how to scroll a random
name across the display::

MicroPython附带一个随机模块，可以轻松地为您的代码引入随机功能。 例如，以下是如何在显示屏上滚动显示随机名称：

    from microbit import *
    import random

    names = ["Mary", "Yolanda", "Damien", "Alia", "Kushal", "Mei Xiu", "Zoltan" ]

    display.scroll(random.choice(names))

The list (``names``) contains seven names defined as strings of characters.
The final line is *nested* (the "onion" effect introduced earlier): the
``random.choice`` method takes the ``names`` list as an argument and returns
an item chosen at random. This item (the randomly chosen name) is the argument
for ``display.scroll``.

列表（names）包含七个定义好的字符串名称。 最后一行是嵌套的（前面介绍的“洋葱”效果）：random.choice方法将names作为参数并返回随机选择的名称；返回的名称（随机选择的名称）又作为display.scroll的参数。

Can you modify the list to include your own set of names?

你能修改列表以包含你自己的名字集吗？

Random Numbers
++++++++++++++

Random numbers are very useful. They're common in games. Why else do we have
dice?

随机数非常有用。 它们在游戏中很常见。 为什么我们有骰子？

MicroPython comes with several useful random number methods. Here's how to
make a simple dice::

MicroPython附带了几个有用的随机数方法。 这是如何产生一个简单骰子的代码：

    from microbit import *
    import random

    display.show(str(random.randint(1, 6)))

Every time the device is reset it displays a number between 1 and 6. You're
starting to get familiar with *nesting*, so it's important to note that
``random.randint`` returns a whole number between the two arguments, inclusive
(a whole number is also called an integer - hence the name of the method).
Notice that because ``display.show`` expects a character then we use the
``str`` function to turn the numeric value into a character (we turn, for
example, ``6`` into ``"6"``).

每次重置设备时，它都会显示一个介于1和6之间的数字。您开始熟悉嵌套，因此请务必注意random.randint返回两个参数之间的整数（整数也称为整型数）。 请注意，因为display.show需要一个字符，所以我们使用str函数将数值转换为一个字符（例如，我们将整数6转换为字符6）。

If you know you'll always want a number between ``0`` and ``N`` then use the
``random.randrange`` method. If you give it a single argument it'll return
random integers up to, but not including, the value of the argument ``N``
(this is different to the behaviour of ``random.randint``).

如果你知道你总是想要一个0到N之间的数字，那么使用random.randrange方法。 如果给它一个参数N，它将返回随机整数，但不包括参数N的值（这与random.randint的功能不同）。

Sometimes you need numbers with a decimal point in them. These are called
*floating point* numbers and it's possible to generate such a number with the
``random.random`` method. This only returns values between ``0.0`` and ``1.0``
inclusive. If you need larger random floating point numbers add the results
of ``random.randrange`` and ``random.random`` like this::

有时您需要带小数点的数字。 这些被称为浮点数，并且可以使用random.random方法生成这样的数字，它仅返回介于0.0和1.0之间的值。 如果您需要更大的随机浮点数，请将random.randrange和random.random返回的结果相加，如下所示：

    from microbit import *
    import random

    answer = random.randrange(100) + random.random()
    display.scroll(str(answer))

Seeds of Chaos
++++++++++++++

The random number generators used by computers are not truly random. They just
give random like results given a starting *seed* value. The seed is often
generated from random-ish values such as the current time and/or readings from
sensors such as the thermometers built into chips.

计算机使用的随机数生成器并不是真正随机的。 它们只是给出一个起始值，然后得出一个类似随机的结果。 起始值通常由当前时间随机产生，或者由内置于芯片中的温度计等传感器的读数产生的。

Sometimes you want to have repeatable random-ish behaviour: a source of
randomness that is reproducible. It's like saying that you need the same five
random values each time you throw a dice.

有时您希望具有可重复的随机行为：可重现的随机源。 这就像说每次掷骰子时你需要相同的五个随机值。

This is easy to achieve by setting the *seed* value. Given a known seed the
random number generator will create the same set of random numbers. The seed is
set with ``random.seed`` and any whole number (integer). This version of the
dice program always produces the same results::

通过设置种子值很容易实现。 给定已知种子，随机数生成器将创建一组相同的随机数。 使用random.seed和任何整数（整型数）设置种子。，此版本的骰子程序始终产生相同的结果：

    from microbit import *
    import random

    random.seed(1337)
    while True:
        if button_a.was_pressed():
            display.show(str(random.randint(1, 6)))

Can you work out why this program needs us to press button A instead of reset
the device as in the first dice example..?

你能弄清楚为什么这个程序需要我们按下按钮A而不是像第一个骰子示例那样重置设备..？
