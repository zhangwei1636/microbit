Music
-----

MicroPython on the BBC micro:bit comes with a powerful music and sound module.
It's very easy to generate bleeps and bloops from the device *if you attach a
speaker*. Use crocodile clips to attach pin 0 and GND to the positive and
negative inputs on the speaker - it doesn't matter which way round they are
connected to the speaker.

BBC micro:bit上的MicroPython配有强大的音乐和声音模块。 如果你连接扬声器， 就会很容易
发出哔哔声和砰砰声。 用鳄鱼夹将引脚0和GND连接到扬声器的正负输入端，扬声器的方向无关紧要。

.. image:: pin0-gnd.png

.. note::

注意：

    Do not attempt this with a Piezo buzzer - such buzzers are only able to
    play a single tone.

    请勿使用Piezo蜂鸣器尝试此操作 - 此类蜂鸣器只能播放单音。

Let's play some music::

我们来播放一些音乐：

    import music

    music.play(music.NYAN)

Notice that we import the ``music`` module. It contains methods used to make
and control sound.

请注意我们导入音乐模块。 它包含有用于制作和控制声音的方法。

MicroPython has quite a lot of built-in melodies. Here's a complete list:

MicroPython有很多内置的音乐。 完整的清单如下：

* ``music.DADADADUM``
* ``music.ENTERTAINER``
* ``music.PRELUDE``
* ``music.ODE``
* ``music.NYAN``
* ``music.RINGTONE``
* ``music.FUNK``
* ``music.BLUES``
* ``music.BIRTHDAY``
* ``music.WEDDING``
* ``music.FUNERAL``
* ``music.PUNCHLINE``
* ``music.PYTHON``
* ``music.BADDY``
* ``music.CHASE``
* ``music.BA_DING``
* ``music.WAWAWAWAA``
* ``music.JUMP_UP``
* ``music.JUMP_DOWN``
* ``music.POWER_UP``
* ``music.POWER_DOWN``

Take the example code and change the melody. Which one is your favourite? How
would you use such tunes as signals or cues?

获取示例代码并更改旋律。 哪一个是你最喜欢的？ 你会如何使用这些曲调作为信号或提示？

Wolfgang Amadeus Microbit
+++++++++++++++++++++++++

Creating your own tunes is easy!

创建自己的曲调很容易！

Each note has a name (like ``C#`` or ``F``), an octave (telling MicroPython how
high or low the note should be played) and a duration (how
long it lasts through time). Octaves are indicated by a number ~ 0 is the
lowest octave, 4 contains middle C and 8 is about as high as you'll ever need
unless you're making music for dogs. Durations are also expressed as numbers.
The higher the value of the duration the longer it will last. Such
values are related to each other - for instance, a duration of ``4`` will last
twice as long as a duration ``2`` (and so on). If you use the note name ``R``
then MicroPython will play a rest (i.e. silence) for the specified duration.

每个音符都有一个名字（比如C＃或F），一个八度（告诉MicroPython应该播放音符的高低）和持
续时间（它持续多长时间）。 八度用数字表示，0表示最低八度，4表示中间C，8度一般不需要，除
非你为狗做音乐。 持续时间也用数字表示。 数值越高，持续时间越长。 这些值彼此相关 - 例如，
持续时间4将两倍于持续时间2（依此类推）。 如果您使用音符名称R，那么MicroPython将在指定的
持续时间内停歇（即静音）。

Each note is expressed as a string of characters like this::

每个音符都表示为一串字符，如下所示：

    NOTE[octave][:duration]

For example, ``"A1:4"`` refers to the note named ``A`` in octave number ``1``
to be played for a duration of ``4``.

例如，A1:4是指在八度音阶1中的A音符，持续时间为4。

Make a list of notes to create a melody (it's equivalent to creating an
animation with a list of images). For example, here's how to make MicroPython
play opening of "Frere Jaques"::

制作音符列表以创建旋律（它相当于创建图像列表的动画）。 例如，以下是如何让MicroPython打开“Frere Jaques”：

    import music

    tune = ["C4:4", "D4:4", "E4:4", "C4:4", "C4:4", "D4:4", "E4:4", "C4:4",
            "E4:4", "F4:4", "G4:8", "E4:4", "F4:4", "G4:8"]
    music.play(tune)

.. note::

注意：

    MicroPython helps you to simplify such melodies. It'll remember the octave
    and duration values until you next change them. As a result, the example
    above can be re-written as::

    MicroPython可以帮助您简化这些旋律。 在您下次更改它们之前，它会记住八度音和持续时间值。
    因此，上面的示例可以重写为：

        import music

        tune = ["C4:4", "D", "E", "C", "C", "D", "E", "C", "E", "F", "G:8",
                "E:4", "F", "G:8"]
        music.play(tune)

    Notice how the octave and duration values only change when they have to.
    It's a lot less typing and simpler to read.

    注意八度音和持续时间值仅在必要时才会改变。 书写较少，阅读也比较简单。

Sound Effects
+++++++++++++

MicroPython lets you make tones that are not musical notes. For example, here'show to create a Police siren effect::

MicroPython可让您制作非音符的音调。 例如，以下是如何创建警笛效果：

    import music

    while True:
        for freq in range(880, 1760, 16):
            music.pitch(freq, 6)
        for freq in range(1760, 880, -16):
            music.pitch(freq, 6)


Notice how the ``music.pitch`` *method* is used in this instance. It expects a
frequency. For example, the frequency of ``440`` is the same as a concert ``A``
used to tune a symphony orchestra.

请注意在这个实例中如何使用music.pitch方法。 它设定一个频率。 就像用440HZ的A音音高来调音交响乐团一样。

In the example above the ``range`` function is used to generate ranges of
numeric values. These numbers are used to define the pitch of the tone. The
three arguments for the ``range`` function are the start value, end value and
step size. Therefore, the first use of ``range`` is saying, in English, "create
a range of numbers between 880 and 1760 in steps of 16". The second use of
``range`` is saying, "create a range of values between 1760 and 880 in steps of
-16". This is how we get a range of frequencies that go up and down in pitch
like a siren.

在上面的示例中，range函数用于生成数值范围。 这些数字用于定义音调的音高。 range函数的三个参数是起始值、结束值和步长。 因此，range的第一种应用是“以16步为单位创建880到1760之间的数字范围”。 range的第二种应用是“以-16的步长创建1760到880之间的范围值”。这就是我们如何获得像警报器的声音升高和下降一样的频率范围。

Because the siren should last forever it's wrapped in an infinite ``while``
loop.

因为它被包裹在无限while循环中，所以警笛应该永远持续鸣响。

Importantly, we have introduced a new sort of a loop inside the ``while``
loop: the ``for`` loop. In English it's like saying, "for each item in some
collection, do some activity with it". Specifically in the example above, it's
saying, "for each frequency in the specified range of frequencies, play the
pitch of that frequency for 6 milliseconds". Notice how the thing to do for
each item in a for loop is indented (as discussed earlier) so Python knows
exactly which code to run to handle the individual items.

重要的是，我们在while循环中引入了一种新的循环：for循环。意思是说“对于满足条件的每一步，用它来循环做一些动作”。 特别是在上面的例子中，就是说，“对于指定频率范围内的每个频率，播放该频率的音调6毫秒”。 请注意，for循环中代码是如何缩进的（如前所述），这样Python就可以确切地知道要运行哪个代码来处理单个项。
