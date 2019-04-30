Network
-------

It is possible to connect devices together to send and receive
messages to and from each other. This is called a network. A network of
interconnected networks is called an internet. The Internet is an internet
of all the internets.

可以将设备连接在一起，互相发送和接收消息。这叫做网络。互相连接的网络称为Internet。互联网是所有连接的Internet网组成。

Networking is hard and this is reflected in the program described below.
However, the beautiful thing about this project is it contains all the common
aspects of network programming you need to know about. It's also remarkably
simple and fun.

联网很困难，这反映在下面的程序中。然而，这个项目的美妙之处在于它包含了您需要了解的网络编程的所有常见方面。它也非常简单和有趣。

But first, let's set the scene...

但首先，让我们来设定场景......

Connection
++++++++++

Imagine a network as a series of layers. At the very bottom is the most
fundamental aspect of communication: there needs to be some sort of way for
a signal to get from one device to the other. Sometimes this is done via a
radio connection, but in this example we're simply going to use two wires.

把网络想象成多层结构。最底层是通信的最基础的物理层：信号需要以某种方式从一个设备传输到另一个设备。有时这是通过无线电连接完成的，但在这个例子中，我们只需要使用两条电线。

.. image:: network.png

It is upon this foundation that we can build all the other layers in the
*network stack*.

正是在这个基础上，我们可以构建网络栈中的所有其他层。

As the diagram shows, blue and red micro:bits are connected via crocodile
leads. Both use pin 1 for output and pin 2 for input. The output from one
device is connected to the input on the other. It's a bit like knowing which
way round to hold a telephone handset - one end has a microphone (the input)
and the other a speaker (the output). The recording of your voice via your
microphone is played out of the other person's speaker. If you hold the
phone the wrong way up, you'll get strange results!

如图所示，蓝色和红色的两块micro:bits通过鳄鱼线连接。两块都使用引脚1作为输出，引脚2作为输入。一个设备的输出连接到另一个设备的输入。这有点像知道的电话手柄一样——一端有麦克风（输入），另一端有扬声器（输出）。通过麦克风录入的声音从另一个手柄的扬声器中播放出来的。如果你拿错电话手柄，会得到奇怪的结果！

It's exactly the same in this instance: you must connect the wires properly!

在这个例子中是完全一样的：你必须正确地连接电线！

Signal
++++++

The next layer in the *network stack* is the signal. Often this will depend
upon the characteristics of the connection. In our example it's simply
digital on and off signals sent down the wires via the IO pins.

网络栈中的下一层是信号。这通常取决于连接的特性。在我们的例子中，它简单通过IO引脚发送开/关数字信号到线上。

If you remember, it's possible to use the IO pins like this::

还记得吗？可以使用IO引脚如下：

    pin1.write_digital(1)  # switch the signal on
    pin1.write_digital(0)  # switch the signal off
    input = pin2.read_digital()  # read the value of the signal (either 1 or 0)

The next step involves describing how to use and handle a signal. For that we
need a...

下一步涉及描述如何使用和处理信号。 为此，我们需要......

Protocol
++++++++

If you ever meet the Queen there are expectations about how you ought to
behave. For example, when she arrives you may bow or curtsey, if she offers her
hand politely shake it, refer to her as "your majesty" and thereafter as
"ma'am" and so on. This set of rules is called the royal protocol. A protocol
explains how to behave given a specific situation (such as meeting the
Queen). A protocol is pre-defined to ensure everyone understands what's going
on before a given situation arises.

如果你遇到过女王，对你的行为就有些预期。例如，当她到达时，你可以鞠躬或行屈膝礼，如果她礼貌地握手，据此可以她称为“陛下”，或者称为“夫人”等等。这套礼节被称为皇家礼仪。协议解释了在特定情况下（如会见女王）如何行事。协议是预先定义的，以确保每个人在特定情况出现之前都了解发生了什么事情。

.. image:: queen.jpg

It is for this reason that we define and use protocols for communicating
messages via a computer network. Computers need to agree before hand how to
send and receive messages. Perhaps the best known protocol is the
hypertext transfer protocol (HTTP) used by the world wide web.

因此，我们定义并使用协议通过计算机网络传递消息。 计算机需要事先商定如何发送和接收消息。 也许最著名的协议是万维网使用的超文本传输协议（HTTP）。

Another famous protocol for sending messages (that pre-dates computers) is
Morse code. It defines how to send character-based messages via on/off signals
of long or short durations. Often such signals are played as bleeps. Long
durations are called dashes (``-``) whereas short durations are dots (``.``).
By combining dashes and dots Morse defines a way to send characters. For
example, here's how the standard Morse alphabet is defined::

另一个著名的发送信息的协议（早于计算机）是莫尔斯电码。它定义了如何通过长或短持续时间的开/关信号发送字符消息。这些信号通常以哔哔声的形式发出。持续时间长的表示破折号（-），而持续时间短的表示点（.）。通过组合破折号和点，莫尔斯定义了一种发送字符的方法。例如，以下是标准莫尔斯字母表的定义方法：

    .-    A     .---  J     ...   S     .----  1      ----.  9
    -...  B     -.-   K     -     T     ..---  2      -----  0
    -.-.  C     .-..  L     ..-   U     ...--  3
    -..   D     --    M     ...-  V     ....-  4
    .     E     -.    N     .--   W     .....  5
    ..-.  F     ---   O     -..-  X     -....  6
    --.   G     .--.  P     -.--  Y     --...  7
    ....  H     --.-  Q     --..  Z     ---..  8
    ..    I     .-.   R

Given the chart above, to send the character "H" the signal is switched on four
times for a short duration, indicating four dots (``....``). For the letter
"L" the signal is also switched on four times, but the second signal has a
longer duration (``.-..``).

如上图所示，要发送字符“H”，短时间信号发生四次，表示四个点（…）。对于字母“L”，信号也发生四次，但第二次是持续时间长的信号（.-..）。

Obviously, the timing of the signal is important: we need to tell a dot from a
dash. That's another point of a protocol, to agree such things so everyone's
implementation of the protocol will work with everyone elses. In this instance
we'll just say that:

显然，信号的时间很重要：我们需要区分短划线和点。相同协议，遵守相同的如本例的要求，则每个人的实现都是一样的。 在本例中，我们要求如下：

* A signal with a duration less than 250 milliseconds is a dot.

* 持续时间小于250毫秒的信号是点。

* A signal with a duration from 250 milliseconds to less than 500 milliseconds is a dash.

* 持续时间从250毫秒到500毫秒的信号是破折号。

* Any other duration of signal is ignored.

* 任何其它信号持续时间都将被忽略。

* A pause / gap in the signal of greater than 500 milliseconds indicates the end of a character.

* 信号中的停顿/间隔超过500毫秒就表示字符结束。

In this way, the sending of a letter "H" is defined as four "on" signals that
last no longer than 250 milliseconds each, followed by a pause of greater than
500 milliseconds (indicating the end of the character).

以这种方式，发送字母“h”被定义为四个“on”信号，每个信号的持续时间不超过250毫秒，随后是一个超过500毫秒的暂停（表示字符结束）。

Message
+++++++

We're finally at a stage where we can build a message - a message that actually
means something to us humans. This is the top-most layer of our *network
stack*.

我们终于到了一个可以建立信息的阶段——实际上是对我们人类的信息。这是我们网络栈的最顶层。

Using the protocol defined above I can send the following sequence of signals
down the physical wire to the other micro:bit::

使用上面定义的协议，可以将以下信号序列沿着物理线发送到另一个micro:bit：

    ...././.-../.-../---/.--/---/.-./.-../-..

Can you work out what it says?

你能明白它说的什么吗？

Application
+++++++++++

It's all very well having a network stack, but you also need a way to
interact with it - some form of application to send and receive messages.
While HTTP is interesting *most* people don't know about it and let their
web-browser handle it - the underlying *network stack* of the world wide web
is hidden (as it should be).

网络栈是非常好的，但是您还需要一种与之交互的方式——某种应用程序用来发送和接收消息。虽然HTTP很有趣，但大多数人并不了解它，而是让他们的Web浏览器来处理它——万维网的底层网络栈是隐藏的（应该是这样）。

So, what sort of application should we write for the BBC micro:bit? How should
it work, from the user's point of view?

那么，我们应该为bbc micro:bit编写什么样的应用程序呢？从用户的角度来看，它应该如何工作？

Obviously, to send a message you should be able to input dots and dashes (we
can use button A for that). If we want to see the message we sent or just
received we should be able to trigger it to scroll across the display (we can
use button B for that). Finally, this being Morse code, if a speaker is
attached, we should be able to play the beeps as a form of aural feedback while
the user is entering their message.

显然，要发送消息，您应该能够输入点和破折号（我们可以使用按钮A）。如果我们想看到我们发送或刚刚收到的信息，我们应该能够触发它在显示屏上滚动（我们可以使用按钮B）。最后，对于莫尔斯电码，如果一个扬声器连接，当用户正在输入这些信息时，我们应该能够听到作为听觉反馈形式的哔哔声。

The End Result
++++++++++++++

Here's the program, in all its glory and annotated with plenty of comments so
you can see what's going on::

这就是这个程序，它的所有荣耀和注释都有很多评论，所以你可以看到发生了什么：

    from microbit import *
    import music


    # A lookup table of morse codes and associated characters.
    MORSE_CODE_LOOKUP = {
        ".-": "A",
        "-...": "B",
        "-.-.": "C",
        "-..": "D",
        ".": "E",
        "..-.": "F",
        "--.": "G",
        "....": "H",
        "..": "I",
        ".---": "J",
        "-.-": "K",
        ".-..": "L",
        "--": "M",
        "-.": "N",
        "---": "O",
        ".--.": "P",
        "--.-": "Q",
        ".-.": "R",
        "...": "S",
        "-": "T",
        "..-": "U",
        "...-": "V",
        ".--": "W",
        "-..-": "X",
        "-.--": "Y",
        "--..": "Z",
        ".----": "1",
        "..---": "2",
        "...--": "3",
        "....-": "4",
        ".....": "5",
        "-....": "6",
        "--...": "7",
        "---..": "8",
        "----.": "9",
        "-----": "0"
    }


    def decode(buffer):
        # Attempts to get the buffer of Morse code data from the lookup table. If
        # it's not there, just return a full stop.
        return MORSE_CODE_LOOKUP.get(buffer, '.')


    # How to display a single dot.
    DOT = Image("00000:"
                "00000:"
                "00900:"
                "00000:"
                "00000:")


    # How to display a single dash.
    DASH = Image("00000:"
                 "00000:"
                 "09990:"
                 "00000:"
                 "00000:")


    # To create a DOT you need to hold the button for less than 250ms.
    DOT_THRESHOLD = 250
    # To create a DASH you need to hold the button for less than 500ms.
    DASH_THRESHOLD = 500


    # Holds the incoming Morse signals.
    buffer = ''
    # Holds the translated Morse as characters.
    message = ''
    # The time from which the device has been waiting for the next keypress.
    started_to_wait = running_time()


    # Put the device in a loop to wait for and react to key presses.
    while True:
        # Work out how long the device has been waiting for a keypress.
        waiting = running_time() - started_to_wait
        # Reset the timestamp for the key_down_time.
        key_down_time = None
        # If button_a is held down, then...
        while button_a.is_pressed():
            # Play a beep - this is Morse code y'know ;-)
            music.pitch(880, 10)
            # Set pin1 (output) to "on"
            pin1.write_digital(1)
            # ...and if there's not a key_down_time then set it to now!
            if not key_down_time:
                key_down_time = running_time()
        # Alternatively, if pin2 (input) is getting a signal, pretend it's a
        # button_a key press...
        while pin2.read_digital():
            if not key_down_time:
                key_down_time = running_time()
        # Get the current time and call it key_up_time.
        key_up_time = running_time()
        # Set pin1 (output) to "off"
        pin1.write_digital(0)
        # If there's a key_down_time (created when button_a was first pressed
        # down).
        if key_down_time:
            # ... then work out for how long it was pressed.
            duration = key_up_time - key_down_time
            # If the duration is less than the max length for a "dot" press...
            if duration < DOT_THRESHOLD:
                # ... then add a dot to the buffer containing incoming Morse codes
                # and display a dot on the display.
                buffer += '.'
                display.show(DOT)
            # Else, if the duration is less than the max length for a "dash"
            # press... (but longer than that for a DOT ~ handled above)
            elif duration < DASH_THRESHOLD:
                # ... then add a dash to the buffer and display a dash.
                buffer += '-'
                display.show(DASH)
            # Otherwise, any other sort of keypress duration is ignored (this isn't
            # needed, but added for "understandability").
            else:
                pass
            # The button press has been handled, so reset the time from which the
            # device is starting to wait for a  button press.
            started_to_wait = running_time()
        # Otherwise, there hasn't been a button_a press during this cycle of the
        # loop, so check there's not been a pause to indicate an end of the
        # incoming Morse code character. The pause must be longer than a DASH
        # code's duration.
        elif len(buffer) > 0 and waiting > DASH_THRESHOLD:
            # There is a buffer and it's reached the end of a code so...
            # Decode the incoming buffer.
            character = decode(buffer)
            # Reset the buffer to empty.
            buffer = ''
            # Show the decoded character.
            display.show(character)
            # Add the character to the message.
            message += character
        # Finally, if button_b was pressed while all the above was going on...
        if button_b.was_pressed():
            # ... display the message,
            display.scroll(message)
            # then reset it to empty (ready for a new message).
            message = ''

How would you improve it? Can you change the definition of a dot and a dash so
speedy Morse code users can use it? What happens if both devices are sending at
the same time? What might you do to handle this situation?

你将如何改进它？你能改变点和破折号的定义，让摩尔斯电码的使用者可以快速使用它？如果两个设备同时发送，会发生什么情况？你会怎么处理这种情况？

.. footer:: The image of Queen Elizabeth II is licensed as per the details here: https://commons.wikimedia.org/wiki/File:Queen_Elizabeth_II_March_2015.jpg
