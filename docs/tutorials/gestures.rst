Gestures (手势)
--------

The really interesting side-effect of having an accelerometer is gesture
detection. If you move your BBC micro:bit in a certain way (as a gesture) then
MicroPython is able to detect this.

加速度计真正有趣的副作用是姿态检测。如果你以某种方式移动你的bbc micro:bit（比如手势），那么micropython就能够检测到这一点。

MicroPython is able to recognise the following gestures: ``up``, ``down``,
``left``, ``right``, ``face up``, ``face down``, ``freefall``, ``3g``, ``6g``,
``8g``, ``shake``. Gestures are always represented as strings. While most of
the names should be obvious, the ``3g``, ``6g`` and ``8g`` gestures apply when
the device encounters these levels of g-force (like when an astronaut is
launched into space).

MicroPython能够识别以下手势：上，下，左，右，面朝上，面朝下，自由落体，3g，6g，8g，摇晃。 手势总是表示为字符串。 虽然大多数名称对应的手势是显而易见的，但是当设备达到这些g-force时（例如当宇航员被发射到太空时），设备就显示3g，6g和8g手势。

To get the current gesture use the ``accelerometer.current_gesture`` method.
Its result is going to be one of the named gestures listed above. For example,
this program will only make your device happy if it is face up::

要获取当前手势，请使用accelerometer.current_gesture方法。 其结果是显示上面列出的命名手势中的一种。 例如，如果它正面朝上，下面程序会显示高兴的脸：

    from microbit import *

    while True:
        gesture = accelerometer.current_gesture()
        if gesture == "face up":
            display.show(Image.HAPPY)
        else:
            display.show(Image.ANGRY)

Once again, because we want the device to react to changing circumstances we
use a ``while`` loop. Within the *scope* of the loop the current gesture is
read and put into ``gesture``. The ``if`` conditional checks if ``gesture`` is
equal to ``"face up"`` (Python uses ``==`` to test for equality, a single
equals sign ``=`` is used for assignment - just like how we assign the gesture
reading to the ``gesture`` object). If the gesture is equal to ``"face up"``
then use the display to show a happy face. Otherwise, the device is made to
look angry!

再者，因为我们希望设备对不断变化的环境做出反应，所以我们使用while循环。在循环体内，读取当前手势并将其放入gesture中。if条件语句检查手势是否等于“正面朝上”（python使用==作为相等运算符，使用单个=符号作为赋值运算符，就像我们如何将手势读数赋值给gesture对象一样）。如果手势等于“face up”，则显示屏显示一张快乐的脸。否则，显示一张生气的脸！

Magic-8
+++++++

A Magic-8 ball is a toy first invented in the 1950s. The idea is to ask
it a yes/no question, shake it and wait for it to reveal the truth. It's rather
easy to turn into a program::

Magic-8球是一种在20世纪50年代首次发明的玩具，其目的是问它一个是/否的问题，摇动它，等待它揭示真相。这种玩具很容易用一个程序来实现：

    from microbit import *
    import random

    answers = [
        "It is certain",
        "It is decidedly so",
        "Without a doubt",
        "Yes, definitely",
        "You may rely on it",
        "As I see it, yes",
        "Most likely",
        "Outlook good",
        "Yes",
        "Signs point to yes",
        "Reply hazy try again",
        "Ask again later",
        "Better not tell you now",
        "Cannot predict now",
        "Concentrate and ask again",
        "Don't count on it",
        "My reply is no",
        "My sources say no",
        "Outlook not so good",
        "Very doubtful",
    ]

    while True:
        display.show("8")
        if accelerometer.was_gesture("shake"):
            display.clear()
            sleep(1000)
            display.scroll(random.choice(answers))

Most of the program is a list called ``answers``. The actual game is in the
``while`` loop at the end.

程序的大部分是一个名为“answer”的列表。实际的游戏在结尾的while循环中。

The default state of the game is to show the character ``"8"``. However, the
program needs to detect if it has been shaken. The ``was_gesture`` method uses
its argument (in this case, the string ``"shake"`` because we want to detect
a shake) to return a ``True`` / ``False`` response. If the device was shaken
the ``if`` conditional drops into its block of code where it clears the screen,
waits for a second (so the device appears to be thinking about your question)
and displays a randomly chosen answer.

游戏默认是显示字符“8”。 但是，该程序需要检测它是否已被摇动。 was_gesture方法根据参数（在本例中是字符串“shake”，因为我们想要检测摇动）以返回响应True / False。 如果设备被摇动，进入if条件语句，首先执行清除屏幕的代码，然后等待一秒钟（表现为设备似乎正在思考您的问题）并显示随机选择的答案。

Why not ask it if this is the greatest program ever written? What could you do
to "cheat" and make the answer always positive or negative? (Hint: use the
buttons.)

为什么不问它是否是曾经写的最伟大的程序？ 你能做些什么来“欺骗”并使答案总是正面或负面的？ （提示：使用按钮。）
