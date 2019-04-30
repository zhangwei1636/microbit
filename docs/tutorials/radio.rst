Radio
-----

Interaction at a distance feels like magic.

远距离的互动感觉像魔术。

Magic might be useful if you're an elf, wizard or unicorn, but such things only
exist in stories.

如果你是一个精灵、巫师或独角兽，魔法可能是有用的，但这些东西只存在于故事中。

However, there's something much better than magic: physics!

然而，还有比魔法更好的东西：物理！

Wireless interaction is all about physics: radio waves (a type of
electromagnetic radiation, similar to visible light) have some sort of property
(such as their amplitude, phase or pulse width) modulated by a transmitter in
such a way that information can be encoded and, thus, broadcast. When radio
waves encounter an electrical conductor (i.e. an aerial), they cause an
alternating current from which the information in the waves can be extracted
and transformed back into its original form.

无线交互都是关于物理的：无线电波（一种电磁辐射，类似于可见光）具有某种属性（例如其振幅、相位或脉宽），通过发射机进行调制，使信息能够被编码，从而进行广播。当无线电波遇到导体（即天线）时，会产生交流电，从中可以提取电波中的信息，并将其解调为原来的形式。

Layers upon Layers
++++++++++++++++++

If you remember, networks are built in layers.

如果你还记得，网络是分层构建的。

The most fundamental requirement for a network is some sort of connection that
allows a signal to get from one device to the other. In our networking
tutorial we used wires connected to the I/O pins. Thanks to the radio module we
can do away with wires and use the physics summarised above as the invisible
connection between devices.

网络最基本的要求是某种连接，允许信号从一个设备传输到另一个设备。在我们的网络教程中，我们使用连接到I/O管脚的电线。由于无线电模块，我们可以去掉电线，将上面概述的无线电波用作设备之间的无线连接。

The next layer up in the network stack is also different from the example in
the networking tutorial. With the wired example we used digital on and off to
send and read a signal from the pins. With the built-in radio on the
micro:bit the smallest useful part of the signal is a byte.

网络栈中的下一层也与网络教程中的示例不同。 通过有线示例，我们使用数字开关来发送和读取引脚的信号。 micro：bit上的内置无线电信号是以一个字节为单位进行发送和接收。

Bytes
+++++

A byte is a unit of information that (usually) consists of eight bits. A bit is
the smallest possible unit of information since it can only be in two states:
on or off.

字节是（通常）由8位组成的信息单位。位是最小的信息单位，因为它只能处于两种状态：开或关。

Bytes work like a sort of abacus: each position in the byte is like a
column in an abacus - they represent an associated number. In an abacus these
are usually thousands, hundreds, tens and units (in UK parlance). In a byte
they are 128, 64, 32, 16, 8, 4, 2 and 1. As bits (on/off
signals) are sent over the air, they are re-combined into bytes by the
recipient.

字节的工作方式类似于算盘：字节中的每个位置都类似于算盘中的一列-它们表示一个关联的数字。在算盘中，通常是千、百、十和个位（用英国的说法）。在一个字节中，它们是128、64、32、16、8、4、2和1。当位（开/关信号）发送空中后，接收端将它们重新组合成字节。

Have you spotted the pattern? (Hint: base 2.)

你发现这种格式吗？ （提示：基数2.）

By adding the numbers associated with the positions in a byte that are set to
"on" we can represent numbers between 0 and 255. The image below shows how this
works with five bits and counting from zero to 32:

通过设置字节中位为1的相关联数字，可以表示0到255之间的数字。下图显示了五个位如何表示零到31：

.. image:: binary_count.gif

If we can agree what each one of the 255 numbers (encoded by a byte) represents ~ such as a character ~ then we can start to send text one character per byte
at a time.

如果我们将256个数字（一个字节编码）中的每一个数字代表一个字符，那么就可以一次一个字符地发送文本。

Funnily enough, people have already
`thought of this <https://en.wikipedia.org/wiki/ASCII>`_ ~ using bytes to
encode and decode information is commonplace. This approximately corresponds to
the Morse-code "protocol" layer in the wired networking example.

有趣的是，人们认为使用字节来编码和解码信息是平常的。这与有线网络示例中的莫尔斯电码“协议”层大致对应。

A really great series of child (and teacher) friendly explanations of "all
things bytes" can be found at the
`CS unplugged <http://csunplugged.org/binary-numbers/>`_ website.

在CS Unplugged网站上可以找到一个非常棒的儿童（和教师）容易理解的解释“万物为字节”系列。

Addressing
++++++++++

The problem with radio is that you can't transmit directly to one person.
Anyone with an appropriate aerial can receive the messages you transmit. As a
result it's important to be able to differentiate who should be receiving
broadcasts.

无线电的问题是你不能直接只传送给一个人。任何有合适天线的人都可以接收你发送的信息。因此，区分接收广播的人很重要。

The way the radio built into the micro:bit solves this problem is quite simple:

内置在micro:bit中的无线电模块解决这个问题的方法非常简单：

* It's possible to tune the radio to different channels (numbered 0-83). This works in exactly the same way as kids' walkie-talkie radios: everyone tunes into the same channel and everyone hears what everyone else broadcasts via that channel. As with walkie-talkies, if you use adjacent channels there is a slight possibility of interference.

* 可以将无线电模块调到不同的频道（编号0-83）。这与儿童对讲机的工作原理完全相同：每个人都调到同一个频道，每个人都能听到其他人通过该频道广播的内容。和对讲机一样，如果你使用相邻的频道，干扰的可能性很小。

* The radio module allows you to specify two pieces of information: an address and a group. The address is like a postal address whereas a group is like a specific recipient at the address. The important thing is the radio will filter out messages that it receives that do not match *your* address and group. As a result, it's important to pre-arrange the address and group your application is going to use.

* 无线电模块允许您指定两条信息：一个地址和一个组。地址类似于邮政地址，而组类似于该地址的特定收件人。重要的是，无线电模块会过滤掉与您的地址和组不匹配的信息。因此，重要的是要预先安排好应用程序要使用的地址和组。

Of course, the micro:bit is still receiving broadcast messages for other
address/group combinations. The important thing is you don't need to worry
about filtering those out. Nevertheless, if someone were clever enough, they
could just read *all the wireless network traffic* no matter what the target
address/group was supposed to be. In this case, it's *essential* to use
encrypted means of communication so only the desired recipient can actually
read the message that was broadcast. Cryptography is a fascinating subject but,
unfortunately, beyond the scope of this tutorial.

当然，micro:bit仍能接收其它地址/组的广播消息。重要的是你不必担心过滤掉那些。然而，如果有人足够聪明，他们也可以读取所有的无线网络流量，不管目标地址/组是什么。在这种情况下，必须使用加密的通信方式，这样只有所需的接收者才能真正收到广播的消息。密码学是一门有趣的学科，但不幸的是，它超出了本教程的范围。

Fireflies （萤火虫）
+++++++++

This is a firefly:

下图是一个萤火虫：

.. image:: firefly.gif

It's a sort of bug that uses bioluminescence to signal (without wires) to its
friends. Here's what they look like when they signal to each other:

这是一种利用生物发光向朋友发出信号（没有电线）的虫子。以下是它们互相发出信号时的样子：

.. image:: fireflies.gif

The BBC have `rather a beautiful video <http://www.bbc.com/earth/story/20160224-worlds-largest-gathering-of-synchronised-fireflies>`_ of fireflies available online.

BBC在网上有一段相当漂亮的萤火虫视频。

We're going to use the radio module to create something akin to a swarm of
fireflies signalling to each other.

我们将使用无线电模块来创建类似于一群萤火虫互相发送信号的东西。

First ``import radio`` to make the functions available to your Python program.
Then call the ``radio.on()`` function to turn the radio on. Since
the radio draws power and takes up memory we've made it so *you* decide
when it is enabled (there is, of course a ``radio.off()`` function).

首先导入无线电模块，使python可以使用它的函数。然后调用radio.on（）函数打开无线电。因为无线电的收发会消耗能量并占用内存，所以我们引入了无线电模块并决定何时启用它（当然还有radio.off（）函数来决定何时关闭它）。

At this point the radio module is configured to sensible defaults that make
it compatible with other platforms that may target the BBC micro:bit. It is
possible to control many of the features discussed above (such as channel and
addressing) as well as the amount of power used to broadcast messages and the
amount of RAM the incoming message queue will take up. The API documentation
contains all the information you need to configure the radio to your needs.

此时，无线电模块配置为适当的默认值，使其与其它使用BBC micro:bit的平台兼容。可以控制上面讨论的许多特性（如通道和寻址），以及用于广播消息的功率和传入消息队列将占用的RAM数量。API文档包含根据需要配置收音机所需的所有信息。

Assuming we're happy with the defaults, the simplest way to send a message is
like this::

假设我们对默认设置满意，发送消息的最简单方法如下：

    radio.send("a message")

The example uses the ``send`` function to simply broadcast the string
"a message". To receive a message is even easier::

该示例使用send函数简单地广播字符串“a message”。接收消息更容易：

    new_message = radio.receive()

As messages are received they are put on a message queue. The ``receive``
function returns the oldest message from the queue as a string, making space
for a new incoming message. If the message queue fills up, then new incoming
messages are ignored.

当接收到消息时，它们被放在消息队列中。receive函数以字符串形式返回队列中最旧的消息，为传入新的消息腾出空间。如果消息队列已满，则忽略新的传入消息。

That's really all there is to it! (Although the radio module is also powerful
enough that you can send any arbitrary type of data, not just strings. See the
API documentation for how this works.)

这就是它的全部！（尽管无线电模块的功能也足够强大，您可以发送任意类型的数据，而不仅仅是字符串。请参阅API文档了解其工作原理。）

Armed with this knowledge, it's simple to make micro:bit fireflies like this:

有了这些知识，制作micro：bit萤火虫很简单：

.. include:: ../../examples/radio.py
    :code: python

The important stuff happens in the event loop. First, it checks if button A was
pressed and, if it was, uses the radio to send the message "flash". Then it
reads any messages from the message queue with ``radio.receive()``. If there is
a message it sleeps a short, random period of time (to make the display more
interesting) and uses ``display.show()`` to animate a firefly flash. Finally,
to make things a bit exciting, it chooses a random number so that it has a 1 in
10 chance of re-broadcasting the "flash" message to anyone else (this is how
it's possible to sustain the firefly display among several devices). If it
decides to re-broadcast then it waits for half a second (so the display from
the initial flash message has chance to die down) before sending
the "flash" signal again. Because this code is enclosed within a ``while True``
block, it loops back to the beginning of the event loop and repeats this
process forever.

主要的事件在事件循环中处理。首先，它检查是否按下了按钮A，如果按下了，则使用无线电模块发送消息“flash”。然后它用radio.receive（）从消息队列中读取消息。如果有消息，它会随机休眠一短时间（以使显示更有趣），并使用display.show（）来显示萤火虫闪光的动画。最后，为了让事情更有趣，它选择了一个随机数，这样它就有1/10的机会向任何其它设备重新广播“flash”消息（这就是怎么能在多个设备中显示萤火虫的可能性）。如果决定重新广播，则在再次发送“flash”信号之前，它会等待半秒钟（这样，初始flash消息的显示才有机会消失）。因为此代码被封闭在while-true块中，所以它将返回到事件循环的开头，并永远重复此过程。

The end result (using a group of micro:bits) should look something like this:

最终结果（使用一组micro:bits）应该如下所示：

.. image:: mb-firefly.gif

.. footer:: The image of binary counting is released under the licensing details listed here: https://en.wikipedia.org/wiki/File:Binary_counter.gif
