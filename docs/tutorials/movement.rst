Movement
--------

Your BBC micro:bit comes with an accelerometer. It measures movement along
three axes:

你的BBC micro：bit附带一个加速度计。 它测量沿三个轴的运动：

* X - tilting from left to right.
* Y - tilting forwards and backwards.
* Z - moving up and down.


* X-从左向右倾斜
* Y-前后倾斜
* Z-上下移动

There is a method for each axis that returns a positive or negative number
indicating a measurement in milli-g's. When the reading is 0 you are "level"
along that particular axis.

每个轴都有一种方法，它返回一个以毫克为单位的正数或负数的测量值。 当其读数为0时，沿着
该特定轴水平运动。

For example, here's a very simple spirit-level that uses ``get_x`` to measure
how level the device is along the X axis::

例如，这里有一个非常简单的水平仪，它使用get_x来测量设备沿x轴的水平情况：

    from microbit import *

    while True:
        reading = accelerometer.get_x()
        if reading > 20:
            display.show("R")
        elif reading < -20:
            display.show("L")
        else:
            display.show("-")

If you hold the device flat it should display ``-``; however, rotate it left or
right and it'll show ``L`` and ``R`` respectively.

如果您将设备平放，它应该显示-；但是，向左或向右旋转它将分别显示L和R。

We want the device to constantly react to change, so we use an
infinite ``while`` loop. The first thing to happen *within the body of the
loop* is a measurement along the X axis which is called ``reading``. Because
the accelerometer is *so* sensitive I've made level +/-20 in range. It's why
the ``if`` and ``elif`` conditionals check for ``> 20`` and ``< -20``. The
``else`` statement means that if the ``reading`` is between -20 and 20 then
we consider it level. For each of these conditions we use the display to show
the appropriate character.

我们希望设备不断地对变化作出反应，所以我们使用无限的while循环。在无限循环体中的第一条语句是沿着x轴测量，这被称为读数。因为设置加速度计的灵敏度范围为+/-20，这就是if和elif条件检查> 20和<-20的原因。else语句意味着如果读数在-20到20之间，那么我们认为它是水平的。而且，满足if语句的每个条件都用display.show显示对应的字符。

There is also a ``get_y`` method for the Y axis and a ``get_z`` method for the
Z axis.

y和z轴分别也有get_y和get_z方法来测量。

If you've ever wondered how a mobile phone knows which up to show the images on
its screen, it's because it uses an accelerometer in exactly the same way as
the program above. Game controllers also contain accelerometers to help you
steer and move around in games.

如果您曾经想知道手机如何知道哪些图像可以在屏幕上显示，那是因为它与上面的程序一样来使用的加速度计。 游戏控制器还包含加速度计，可帮助您在游戏中转向和移动。

Musical Mayhem
++++++++++++++

One of the most wonderful aspects of MicroPython on the BBC micro:bit is how it
lets you easily link different capabilities of the device together. For
example, let's turn it into a musical instrument (of sorts).

BBC micro：bit上的MicroPython最精彩的一个方面就是它可以让你轻松地将设备的不同功能连接在一起。 例如，把设备变成一种乐器（各种各样）。

Connect a speaker as you did in the music tutorial. Use crocodile clips to
attach pin 0 and GND to the positive and negative inputs on the speaker - it
doesn't matter which way round they are connected to the speaker.

像music教程说明连接扬声器，用鳄鱼夹将pin0和GND连接到扬声器的正负极上-不要在意连接到扬声器上的方法。

.. image:: pin0-gnd.png

What happens if we take the readings from the accelerometer and play them as
pitches? Let's find out::

如果我们从加速度计读取读数并将其作为音高播放会发生什么？ 我们来看看：

    from microbit import *
    import music

    while True:
        music.pitch(accelerometer.get_y(), 10)

The key line is at the end and remarkably simple. We *nest* the reading from
the Y axis as the frequency to feed into the ``music.pitch`` method. We only
let it play for 10 milliseconds because we want the tone to change quickly as
the device is tipped. Because the device is in an infinite ``while`` loop it
is constantly reacting to changes in the Y axis measurement.

关键的最后一行非常简单。我们嵌套的加速度计读取Y轴的数据，就像给music.pitch设置一个种子频率一样。我们只让它持续10毫秒时间，因为我们想音调改变跟设备翻转一样快。设备通过无限while循环来时时读取Y轴的测量数据。

That's it!

就是这样！

Tip the device forwards and backwards. If the reading along the Y axis is
positive it'll change the pitch of the tone played by the micro:bit.

前后倾斜设备，如果Y轴的读数是正，micro:bit就会改变音调的音量

Imagine a whole symphony orchestra of these devices. Can you play a tune? How
would you improve the program to make the micro:bit sound more musical?

想象一个由这些装置组成的交响乐团。你会弹一首曲子吗？你将如何改进这个程序，使micro:bit的声音听起来更具有音乐性？
