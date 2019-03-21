Images
------

MicroPython is about as good at art as you can be if the only thing you have is
a 5x5 grid of red LEDs (light emitting diodes - the things that light up on the
front of the device). MicroPython gives you quite a lot of control over the
display so you can create all sorts of interesting effects.

如果你只有的是5x5红色LED点阵（发光二极管 - 设备前面点亮的东西），那么MicroPython在
艺术上的表现就和你能做到的一样好了。 MicroPython提供了很多对显示的控制，因此你可以
创建各种有趣的效果。

MicroPython comes with lots of built-in pictures to show on the display.
For example, to make the device appear happy you type::

MicroPython附带了许多内置图片可在显示屏上显示。 例如，要使设备显示开心，请键入：

    from microbit import *
    display.show(Image.HAPPY)

I suspect you can remember what the first line does. The second line uses the
``display`` object to ``show`` a built-in image. The happy image we want to
display is a part of the ``Image`` object and called ``HAPPY``. We tell
``show`` to use it by putting it between the parenthesis (``(`` and ``)``).

还记得第一行的作用吧。第二行使用display对象的show方法显示内置图像。我们要显示的快乐图像是Image对象的一部分，名称为“HAPPY”。我们在Show方法的括号中输入“Image.HAPPY”。

.. image:: happy.png

Here's a list of the built-in images:

这是内置图像的列表：

    * ``Image.HEART``
    * ``Image.HEART_SMALL``
    * ``Image.HAPPY``
    * ``Image.SMILE``
    * ``Image.SAD``
    * ``Image.CONFUSED``
    * ``Image.ANGRY``
    * ``Image.ASLEEP``
    * ``Image.SURPRISED``
    * ``Image.SILLY``
    * ``Image.FABULOUS``
    * ``Image.MEH``
    * ``Image.YES``
    * ``Image.NO``
    * ``Image.CLOCK12``, ``Image.CLOCK11``, ``Image.CLOCK10``, ``Image.CLOCK9``,
      ``Image.CLOCK8``, ``Image.CLOCK7``, ``Image.CLOCK6``, ``Image.CLOCK5``,
      ``Image.CLOCK4``, ``Image.CLOCK3``, ``Image.CLOCK2``, ``Image.CLOCK1``
    * ``Image.ARROW_N``, ``Image.ARROW_NE``, ``Image.ARROW_E``,
      ``Image.ARROW_SE``, ``Image.ARROW_S``, ``Image.ARROW_SW``,
      ``Image.ARROW_W``, ``Image.ARROW_NW``
    * ``Image.TRIANGLE``
    * ``Image.TRIANGLE_LEFT``
    * ``Image.CHESSBOARD``
    * ``Image.DIAMOND``
    * ``Image.DIAMOND_SMALL``
    * ``Image.SQUARE``
    * ``Image.SQUARE_SMALL``
    * ``Image.RABBIT``
    * ``Image.COW``
    * ``Image.MUSIC_CROTCHET``
    * ``Image.MUSIC_QUAVER``
    * ``Image.MUSIC_QUAVERS``
    * ``Image.PITCHFORK``
    * ``Image.XMAS``
    * ``Image.PACMAN``
    * ``Image.TARGET``
    * ``Image.TSHIRT``
    * ``Image.ROLLERSKATE``
    * ``Image.DUCK``
    * ``Image.HOUSE``
    * ``Image.TORTOISE``
    * ``Image.BUTTERFLY``
    * ``Image.STICKFIGURE``
    * ``Image.GHOST``
    * ``Image.SWORD``
    * ``Image.GIRAFFE``
    * ``Image.SKULL``
    * ``Image.UMBRELLA``
    * ``Image.SNAKE``

There's quite a lot! Why not modify the code that makes the micro:bit look
happy to see what some of the other built-in images look like? (Just replace
``Image.HAPPY`` with one of the built-in images listed above.)

有很多！ 为什么不修改使代码使micro:bit看起来很高兴看到其他一些内置图像是什么样的？
（只需将Image.HAPPY替换为上面列出的其中一个内置图像。）

DIY Images
++++++++++

Of course, you want to make your own image to display on the micro:bit, right?

当然，你想让你自己的图像显示在micro：bit上，对吧？

That's easy.

容易

Each LED pixel on the physical display can be set to one of ten values. If a
pixel is set to ``0`` (zero) then it's off. It literally has zero brightness.
However, if it is set to ``9`` then it is at its brightest level. The values
``1`` to ``8`` represent the brightness levels between off (``0``) and full on
(``9``).

物理显示屏上的每个LED像素可以设置为十个值中的一个。 如果像素设置为0（零）则LED关闭。
LED实际上有零亮度。 当然，如果它设置为9，那么它LED处于最亮的水平。 值1到8表示关闭（0）
和完全打开（9）之间的亮度级别。

Armed with this information, it's possible to create a new image like this::

有了这些信息，就可以创建一个像这样的新图像：

    from microbit import *

    boat = Image("05050:"
                 "05050:"
                 "05050:"
                 "99999:"
                 "09990")

    display.show(boat)

(When run, the device should display an old-fashioned "Blue Peter" sailing ship
with the masts dimmer than the boat's hull.)

（运行时，设备应显示一艘老式的“蓝色彼得”号帆船，其桅杆比船体更暗。）

Have you figured out how to draw a picture? Have you noticed that each line of
the physical display is represented by a line of numbers ending in ``:`` and
enclosed between ``"`` double quotes? Each number specifies a brightness.
There are five lines of five numbers so it's possible to specify the individual
brightness for each of the five pixels on each of the five lines on the
physical display. That's how to create a new image.

Simple!

你知道如何画一幅画吗？ 您是否注意到物理显示的每一行都用以“：”结尾一行数字表示，并用双引号括起来？每个数字指定一个亮度。有五行，每行五个数字，因此每个数字表示显示屏中一个像素的亮度。这就是如何创建一个新图像。

简单！

In fact, you don't need to write this over several lines. If you think you can
keep track of each line, you can rewrite it like this::

实际上，您不需要写多行。 如果您认为可以跟踪每一行，可以重写如下：

    boat = Image("05050:05050:05050:99999:09990")

Animation  动画
+++++++++

Static images are fun, but it's even more fun to make them move. This is also
amazingly simple to do with MicroPython ~ just use a list of images!

静态图像很有趣，但让它们移动会更有趣。 这在使用MicroPython也非常简单?只需使用图像列表！

Here is a shopping list::

这是一个购物清单：

    Eggs
    Bacon
    Tomatoes

Here's how you'd represent this list in Python::

以下是在Python中表示此清单的方式：

    shopping = ["Eggs", "Bacon", "Tomatoes" ]

I've simply created a list called ``shopping`` and it contains three items.
Python knows it's a list because it's enclosed in square brackets (``[`` and
``]``). Items in the list are separated by a comma (``,``) and in this instance
the items are three strings of characters: ``"Eggs"``, ``"Bacon"`` and
``"Tomatoes"``. We know they are strings of characters because they're enclosed
in quotation marks ``"``.

我简单创建了一个名为shopping的列表，它包含三个项目。 Python知道它是一个列表，因为它括在方括号[]中。 列表中的项目用逗号（，）分隔，在这个例子中，项目是三个字符串：“Eggs”，“Bacon”和“Tomatoes”。 我们知道它们是字符串，因为它们用双引号括起来。

You can store anything in a list with Python. Here's a list of numbers::

您可以使用Python将任何内容存储在列表中。 这是一个数字列表：

    primes = [2, 3, 5, 7, 11, 13, 17, 19]


.. note::

注意：

    Numbers don't need to be quoted since they represent a value (rather than a
    string of characters). It's the difference between ``2`` (the numeric value
    2) and ``"2"`` (the character/digit representing the number 2). Don't worry
    if this doesn't make sense right now. You'll soon get used to it.

    数字不需要引号，因为它们代表一个值（而不是一串字符）。 2（数值2）和“2”（表示数字2的字符/数字）是不一样的。 如果现在不      理解，请不要担心，你很快就会理解它。

It's even possible to store different sorts of things in the same list::

甚至可以在同一个列表中存储不同类型的数据：

    mixed_up_list = ["hello!", 1.234, Image.HAPPY]

Notice that last item? It was an image!

注意最后一项？ 这是一张图片！

We can tell MicroPython to animate a list of images. Luckily we have a
couple of lists of images already built in. They're called ``Image.ALL_CLOCKS``
and ``Image.ALL_ARROWS``::

我们可以告诉MicroPython为图像列表设置动画。 幸运的是，我们已经内置了几个图像列表。它们被称为Image.ALL_CLOCKS和Image.ALL_ARROWS：

    from microbit import *

    display.show(Image.ALL_CLOCKS, loop=True, delay=100)

As with a single image, we use ``display.show`` to show it on the
device's display. However, we tell MicroPython to use ``Image.ALL_CLOCKS`` and
it understands that it needs to show each image in the list, one after the
other. We also tell MicroPython to keep looping over the list of images (so
the animation lasts forever) by saying ``loop=True``. Furthermore, we tell it
that we want the delay between each image to be only 100 milliseconds (a tenth
of a second) with the argument ``delay=100``.

与单个图像一样，我们使用display.show在设备的显示屏上显示它。 但是，我们告诉MicroPython使
用Image.ALL_CLOCKS，它知道它需要一个接一个地显示列表中的每个图像。 我们还告诉MicroPython通
过设置loop = True来循环遍历图像列表（因此动画永远持续）。 此外，我们通过设置delay=100参数来使每个图像之
间的延迟为100毫秒（十分之一秒）。

Can you work out how to animate over the ``Image.ALL_ARROWS`` list? How do you
avoid looping forever (hint: the opposite of ``True`` is ``False`` although
the default value for ``loop`` is ``False``)? Can you change the speed of the
animation?

你能弄清楚如何在Image.ALL_ARROWS列表上制作动画吗？ 你如何避免永远循环（提示：虽然
loop的默认值是False，但True的反义是假的）？ 你能改变动画的速度吗？

Finally, here's how to create your own animation. In my example I'm going to
make my boat sink into the bottom of the display::

最后，这是如何创建自己的动画。 在我的例子中，我要让我的船沉入显示屏的底部：

    from microbit import *

    boat1 = Image("05050:"
                  "05050:"
                  "05050:"
                  "99999:"
                  "09990")

    boat2 = Image("00000:"
                  "05050:"
                  "05050:"
                  "05050:"
                  "99999")

    boat3 = Image("00000:"
                  "00000:"
                  "05050:"
                  "05050:"
                  "05050")

    boat4 = Image("00000:"
                  "00000:"
                  "00000:"
                  "05050:"
                  "05050")

    boat5 = Image("00000:"
                  "00000:"
                  "00000:"
                  "00000:"
                  "05050")

    boat6 = Image("00000:"
                  "00000:"
                  "00000:"
                  "00000:"
                  "00000")

    all_boats = [boat1, boat2, boat3, boat4, boat5, boat6]
    display.show(all_boats, delay=200)

Here's how the code works:

以下是代码说明：

* I create six ``boat`` images in exactly the same way I described above.
* 我创建六个船图像，与我上面描述的完全相同。

* Then, I put them all into a list that I call ``all_boats``.
* 然后，我将它们全部放入一个名为all_boats的列表中。

* Finally, I ask ``display.show`` to animate the list with a delay of 200 milliseconds.
* 最后，用display.show以200毫秒的延迟为列表设置动画。

* Since I've not set ``loop=True`` the boat will only sink once (thus making my animation scientifically accurate). :-)
* 因为没有设置loop = True，所以船只只会下沉一次（从而使我的动画在科学上更加准确）。

What would you animate? Can you animate special effects? How would you make an
image fade out and then fade in again?

你会什么动画？ 你可以做动画特效吗？ 如何使图像淡出然后再次淡入？
