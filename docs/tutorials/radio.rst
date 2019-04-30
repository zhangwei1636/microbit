Radio
-----

Interaction at a distance feels like magic.

Զ����Ļ����о���ħ����

Magic might be useful if you're an elf, wizard or unicorn, but such things only
exist in stories.

�������һ�����顢��ʦ������ޣ�ħ�����������õģ�����Щ����ֻ�����ڹ����С�

However, there's something much better than magic: physics!

Ȼ�������б�ħ�����õĶ���������

Wireless interaction is all about physics: radio waves (a type of
electromagnetic radiation, similar to visible light) have some sort of property
(such as their amplitude, phase or pulse width) modulated by a transmitter in
such a way that information can be encoded and, thus, broadcast. When radio
waves encounter an electrical conductor (i.e. an aerial), they cause an
alternating current from which the information in the waves can be extracted
and transformed back into its original form.

���߽������ǹ�������ģ����ߵ粨��һ�ֵ�ŷ��䣬�����ڿɼ��⣩����ĳ�����ԣ��������������λ��������ͨ����������е��ƣ�ʹ��Ϣ�ܹ������룬�Ӷ����й㲥�������ߵ粨�������壨�����ߣ�ʱ������������磬���п�����ȡ�粨�е���Ϣ����������Ϊԭ������ʽ��

Layers upon Layers
++++++++++++++++++

If you remember, networks are built in layers.

����㻹�ǵã������Ƿֲ㹹���ġ�

The most fundamental requirement for a network is some sort of connection that
allows a signal to get from one device to the other. In our networking
tutorial we used wires connected to the I/O pins. Thanks to the radio module we
can do away with wires and use the physics summarised above as the invisible
connection between devices.

�����������Ҫ����ĳ�����ӣ������źŴ�һ���豸���䵽��һ���豸�������ǵ�����̳��У�����ʹ�����ӵ�I/O�ܽŵĵ��ߡ��������ߵ�ģ�飬���ǿ���ȥ�����ߣ���������������ߵ粨�����豸֮����������ӡ�

The next layer up in the network stack is also different from the example in
the networking tutorial. With the wired example we used digital on and off to
send and read a signal from the pins. With the built-in radio on the
micro:bit the smallest useful part of the signal is a byte.

����ջ�е���һ��Ҳ������̳��е�ʾ����ͬ�� ͨ������ʾ��������ʹ�����ֿ��������ͺͶ�ȡ���ŵ��źš� micro��bit�ϵ��������ߵ��ź�����һ���ֽ�Ϊ��λ���з��ͺͽ��ա�

Bytes
+++++

A byte is a unit of information that (usually) consists of eight bits. A bit is
the smallest possible unit of information since it can only be in two states:
on or off.

�ֽ��ǣ�ͨ������8λ��ɵ���Ϣ��λ��λ����С����Ϣ��λ����Ϊ��ֻ�ܴ�������״̬������ء�

Bytes work like a sort of abacus: each position in the byte is like a
column in an abacus - they represent an associated number. In an abacus these
are usually thousands, hundreds, tens and units (in UK parlance). In a byte
they are 128, 64, 32, 16, 8, 4, 2 and 1. As bits (on/off
signals) are sent over the air, they are re-combined into bytes by the
recipient.

�ֽڵĹ�����ʽ���������̣��ֽ��е�ÿ��λ�ö������������е�һ��-���Ǳ�ʾһ�����������֡��������У�ͨ����ǧ���١�ʮ�͸�λ����Ӣ����˵��������һ���ֽ��У�������128��64��32��16��8��4��2��1����λ����/���źţ����Ϳ��к󣬽��ն˽�����������ϳ��ֽڡ�

Have you spotted the pattern? (Hint: base 2.)

�㷢�����ָ�ʽ�� ����ʾ������2.��

By adding the numbers associated with the positions in a byte that are set to
"on" we can represent numbers between 0 and 255. The image below shows how this
works with five bits and counting from zero to 32:

ͨ�������ֽ���λΪ1����������֣����Ա�ʾ0��255֮������֡���ͼ��ʾ�����λ��α�ʾ�㵽31��

.. image:: binary_count.gif

If we can agree what each one of the 255 numbers (encoded by a byte) represents ~ such as a character ~ then we can start to send text one character per byte
at a time.

������ǽ�256�����֣�һ���ֽڱ��룩�е�ÿһ�����ִ���һ���ַ�����ô�Ϳ���һ��һ���ַ��ط����ı���

Funnily enough, people have already
`thought of this <https://en.wikipedia.org/wiki/ASCII>`_ ~ using bytes to
encode and decode information is commonplace. This approximately corresponds to
the Morse-code "protocol" layer in the wired networking example.

��Ȥ���ǣ�������Ϊʹ���ֽ�������ͽ�����Ϣ��ƽ���ġ�������������ʾ���е�Ī��˹���롰Э�顱����¶�Ӧ��

A really great series of child (and teacher) friendly explanations of "all
things bytes" can be found at the
`CS unplugged <http://csunplugged.org/binary-numbers/>`_ website.

��CS Unplugged��վ�Ͽ����ҵ�һ���ǳ����Ķ�ͯ���ͽ�ʦ���������Ľ��͡�����Ϊ�ֽڡ�ϵ�С�

Addressing
++++++++++

The problem with radio is that you can't transmit directly to one person.
Anyone with an appropriate aerial can receive the messages you transmit. As a
result it's important to be able to differentiate who should be receiving
broadcasts.

���ߵ���������㲻��ֱ��ֻ���͸�һ���ˡ��κ��к������ߵ��˶����Խ����㷢�͵���Ϣ����ˣ����ֽ��չ㲥���˺���Ҫ��

The way the radio built into the micro:bit solves this problem is quite simple:

������micro:bit�е����ߵ�ģ�����������ķ����ǳ��򵥣�

* It's possible to tune the radio to different channels (numbered 0-83). This works in exactly the same way as kids' walkie-talkie radios: everyone tunes into the same channel and everyone hears what everyone else broadcasts via that channel. As with walkie-talkies, if you use adjacent channels there is a slight possibility of interference.

* ���Խ����ߵ�ģ�������ͬ��Ƶ�������0-83���������ͯ�Խ����Ĺ���ԭ����ȫ��ͬ��ÿ���˶�����ͬһ��Ƶ����ÿ���˶�������������ͨ����Ƶ���㲥�����ݡ��ͶԽ���һ���������ʹ�����ڵ�Ƶ�������ŵĿ����Ժ�С��

* The radio module allows you to specify two pieces of information: an address and a group. The address is like a postal address whereas a group is like a specific recipient at the address. The important thing is the radio will filter out messages that it receives that do not match *your* address and group. As a result, it's important to pre-arrange the address and group your application is going to use.

* ���ߵ�ģ��������ָ��������Ϣ��һ����ַ��һ���顣��ַ������������ַ�����������ڸõ�ַ���ض��ռ��ˡ���Ҫ���ǣ����ߵ�ģ�����˵������ĵ�ַ���鲻ƥ�����Ϣ����ˣ���Ҫ����ҪԤ�Ȱ��ź�Ӧ�ó���Ҫʹ�õĵ�ַ���顣

Of course, the micro:bit is still receiving broadcast messages for other
address/group combinations. The important thing is you don't need to worry
about filtering those out. Nevertheless, if someone were clever enough, they
could just read *all the wireless network traffic* no matter what the target
address/group was supposed to be. In this case, it's *essential* to use
encrypted means of communication so only the desired recipient can actually
read the message that was broadcast. Cryptography is a fascinating subject but,
unfortunately, beyond the scope of this tutorial.

��Ȼ��micro:bit���ܽ���������ַ/��Ĺ㲥��Ϣ����Ҫ�����㲻�ص��Ĺ��˵���Щ��Ȼ������������㹻����������Ҳ���Զ�ȡ���е�������������������Ŀ���ַ/����ʲô������������£�����ʹ�ü��ܵ�ͨ�ŷ�ʽ������ֻ������Ľ����߲��������յ��㲥����Ϣ������ѧ��һ����Ȥ��ѧ�ƣ������ҵ��ǣ��������˱��̵̳ķ�Χ��

Fireflies ��ө��棩
+++++++++

This is a firefly:

��ͼ��һ��ө��棺

.. image:: firefly.gif

It's a sort of bug that uses bioluminescence to signal (without wires) to its
friends. Here's what they look like when they signal to each other:

����һ���������﷢�������ѷ����źţ�û�е��ߣ��ĳ��ӡ����������ǻ��෢���ź�ʱ�����ӣ�

.. image:: fireflies.gif

The BBC have `rather a beautiful video <http://www.bbc.com/earth/story/20160224-worlds-largest-gathering-of-synchronised-fireflies>`_ of fireflies available online.

BBC��������һ���൱Ư����ө�����Ƶ��

We're going to use the radio module to create something akin to a swarm of
fireflies signalling to each other.

���ǽ�ʹ�����ߵ�ģ��������������һȺө��滥�෢���źŵĶ�����

First ``import radio`` to make the functions available to your Python program.
Then call the ``radio.on()`` function to turn the radio on. Since
the radio draws power and takes up memory we've made it so *you* decide
when it is enabled (there is, of course a ``radio.off()`` function).

���ȵ������ߵ�ģ�飬ʹpython����ʹ�����ĺ�����Ȼ�����radio.on�������������ߵ硣��Ϊ���ߵ���շ�������������ռ���ڴ棬�����������������ߵ�ģ�鲢������ʱ����������Ȼ����radio.off����������������ʱ�ر�������

At this point the radio module is configured to sensible defaults that make
it compatible with other platforms that may target the BBC micro:bit. It is
possible to control many of the features discussed above (such as channel and
addressing) as well as the amount of power used to broadcast messages and the
amount of RAM the incoming message queue will take up. The API documentation
contains all the information you need to configure the radio to your needs.

��ʱ�����ߵ�ģ������Ϊ�ʵ���Ĭ��ֵ��ʹ��������ʹ��BBC micro:bit��ƽ̨���ݡ����Կ����������۵�������ԣ���ͨ����Ѱַ�����Լ����ڹ㲥��Ϣ�Ĺ��ʺʹ�����Ϣ���н�ռ�õ�RAM������API�ĵ�����������Ҫ���������������������Ϣ��

Assuming we're happy with the defaults, the simplest way to send a message is
like this::

�������Ƕ�Ĭ���������⣬������Ϣ����򵥷������£�

    radio.send("a message")

The example uses the ``send`` function to simply broadcast the string
"a message". To receive a message is even easier::

��ʾ��ʹ��send�����򵥵ع㲥�ַ�����a message����������Ϣ�����ף�

    new_message = radio.receive()

As messages are received they are put on a message queue. The ``receive``
function returns the oldest message from the queue as a string, making space
for a new incoming message. If the message queue fills up, then new incoming
messages are ignored.

�����յ���Ϣʱ�����Ǳ�������Ϣ�����С�receive�������ַ�����ʽ���ض�������ɵ���Ϣ��Ϊ�����µ���Ϣ�ڳ��ռ䡣�����Ϣ����������������µĴ�����Ϣ��

That's really all there is to it! (Although the radio module is also powerful
enough that you can send any arbitrary type of data, not just strings. See the
API documentation for how this works.)

���������ȫ�������������ߵ�ģ��Ĺ���Ҳ�㹻ǿ�������Է����������͵����ݣ������������ַ����������API�ĵ��˽��乤��ԭ����

Armed with this knowledge, it's simple to make micro:bit fireflies like this:

������Щ֪ʶ������micro��bitө���ܼ򵥣�

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

��Ҫ���¼����¼�ѭ���д������ȣ�������Ƿ����˰�ťA����������ˣ���ʹ�����ߵ�ģ�鷢����Ϣ��flash����Ȼ������radio.receive��������Ϣ�����ж�ȡ��Ϣ���������Ϣ�������������һ��ʱ�䣨��ʹ��ʾ����Ȥ������ʹ��display.show��������ʾө�������Ķ��������Ϊ�����������Ȥ����ѡ����һ�������������������1/10�Ļ������κ������豸���¹㲥��flash����Ϣ���������ô���ڶ���豸����ʾө���Ŀ����ԣ�������������¹㲥�������ٴη��͡�flash���ź�֮ǰ������ȴ������ӣ���������ʼflash��Ϣ����ʾ���л�����ʧ������Ϊ�˴��뱻�����while-true���У������������ص��¼�ѭ���Ŀ�ͷ������Զ�ظ��˹��̡�

The end result (using a group of micro:bits) should look something like this:

���ս����ʹ��һ��micro:bits��Ӧ��������ʾ��

.. image:: mb-firefly.gif

.. footer:: The image of binary counting is released under the licensing details listed here: https://en.wikipedia.org/wiki/File:Binary_counter.gif
