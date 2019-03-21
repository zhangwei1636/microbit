Input/Output
------------

There are strips of metal along the bottom edge of the BBC micro:bit that make
it look as if the device has teeth. These are the input/output pins (or I/O pins
for short).

BBC micro：bit的底边有金属条，看起来好像牙齿。 这些是输入/输出引脚（或简称I / O引脚）。

.. image:: blue-microbit.png

Some of the pins are bigger than others so it's possible to attach crocodile
clips to them. These are the ones labelled 0, 1, 2, 3V and GND (computers
always start counting from zero). If you attach an edge connector board to the
device it's possible to plug in wires connected to the other (smaller) pins.

有些针脚比其他针脚大，所以可以将鳄鱼夹子连接到它们上面。 这些针脚标记为0,1,2,3V和GND
（计算机始终从零开始计数）。如果将边缘连接器板连接到设备，则可以插入连接到其他（较小）
引脚的电线。

Each pin on the BBC micro:bit is represented by an *object* called ``pinN``
where ``N`` is the pin number. So, for example, to do things with the pin
labelled with a 0 (zero), use the object called ``pin0``.

BBC micro：bit上的每个引脚由称为pinN的对象表示，其中N是引脚编号。 因此，假如要对标
有0（零）的引脚执行操作，就使用名为pin0的对象。

Simple!

These objects have various *methods* associated with them depending upon what
the specific pin is capable of.

这些对象具有与之相关联的各种方法，具体取决于特定管脚的功能。

Ticklish Python

+++++++++++++++

（怕痒的Python）

The simplest example of input via the pins is a check to see if they are
touched. So, you can tickle your device to make it laugh like this::

引脚输入的最简单示例是检查它们是否被触摸。 所以，让设备像这样笑：

    from microbit import *

    while True:
        if pin0.is_touched():
            display.show(Image.HAPPY)
        else:
            display.show(Image.SAD)

With one hand, hold your device by the GND pin. Then, with your other hand,
touch (or tickle) the 0 (zero) pin. You should see the display change from
grumpy to happy!

用一只手握住GND引脚。 然后用另一只手触摸（或挠痒）0（零）引脚。 您应该看到显
示从发怒变为快乐！

This is a form of very basic input measurement. However, the fun really starts
when you plug in circuits and other devices via the pins.

这是一种非常基本的输入测量方式。 然而，当您通过引脚接入电路和其他设备时，真正
的乐趣就开始了。

Bleeps and Bloops
+++++++++++++++++

The simplest thing we can attach to the device is a Piezo buzzer. We're going
to use it for output.

连接到设备上的最简单的东西是Piezo蜂鸣器。 我们把它用于输出。

.. image:: piezo_buzzer.jpg

These small devices play a high-pitched bleep when connected to a circuit. To
attach one to your BBC micro:bit you should attach crocodile clips to pin 0 and
GND (as shown below).

当蜂鸣器连接到设备时会发出高音调的嘟嘟声。 用鳄鱼夹将蜂鸣器连接到BBC micro：bit的
引脚0和GND（如下图所示）。

.. image:: pin0-gnd.png

The wire from pin 0 should be attached to the positive connector on the buzzer
and the wire from GND to the negative connector.

引脚0应连接到蜂鸣器上的正极，GND连接到负极。

The following program will cause the buzzer to make a sound::

以下程序将使蜂鸣器发出声音：

    from microbit import *

    pin0.write_digital(1)

This is fun for about 5 seconds and then you'll want to make the horrible
squeaking stop. Let's improve our example and make the device bleep::

这很有趣，大约5秒钟，然后你会想要让可怕的吱吱声停止。 让我们改进示例并使设备发出哔哔声：

    from microbit import *

    while True:
        pin0.write_digital(1)
        sleep(20)
        pin0.write_digital(0)
        sleep(480)

Can you work out how this script works? Remember that ``1`` is "on" and ``0``
is "off" in the digital world.

你能弄清楚这个脚本是如何工作的吗？ 请记住，数字世界中1是“开”，0是“关”。

The device is put into an infinite loop and immediately switches pin 0 on. This
causes the buzzer to emit a beep. While the buzzer is beeping, the device
sleeps for twenty milliseconds and then switches pin 0 off. This gives the
effect of a short bleep. Finally, the device sleeps for 480 milliseconds before
looping back and starting all over again. This means you'll get two bleeps per
second (one every 500 milliseconds).

程序进入无限循环并立即开启引脚0。 这会使蜂鸣器发出蜂鸣声。 当蜂鸣器发出蜂鸣声时，设备会休眠20毫秒，然后关闭引脚0。 这会产生短暂的哔哔声。 最后，设备会在循环返回并重新开始之前休眠480毫秒。 这意味着你每秒会得到两次哔哔声（每500毫秒一次）。

We've made a very simple metronome!

我们制作了一个非常简单的节拍器！

.. footer:: The image of the pizeo buzzer is CC BY-NC-SA 3.0 from https://www.flickr.com/photos/tronixstuff/4821350094
