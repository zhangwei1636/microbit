Image 图片
*****

.. py:module:: microbit

The ``Image`` class is used to create images that can be displayed easily on
the device's LED matrix. Given an image object it's possible to display it via
the ``display`` API::

Image类用于创建可在设备的LED矩阵上轻松显示的图片。对于图像对象，可以通过display API显示它：

    display.show(Image.HAPPY)

.. image:: image-smile.png

There are four ways in which you can construct an image:

有四种方法可以构建图片：

- ``Image()`` - Create a blank 5x5 image

-Image() - 建立一个5X5的空白图片

- ``Image(string)`` - Create an image by parsing the string, a single character
  returns that glyph

-Image(string) - 通过解析字符串来创建图片，单个字符返回该字形

- ``Image(width, height)`` - Create a blank image of given size

-Image(width, height) - 建立指定大小的图片

- ``Image(width, height, buffer)`` - Create an image from the given buffer

-Image(width, height, buffer) - 从给定缓冲区创建图片


Classes 类
=======

.. py:class::
    Image(string)
    Image(width=None, height=None, buffer=None)

    If ``string`` is used, it has to consist of digits 0-9 arranged into
    lines, describing the image, for example::

    如果使用字符串，则必须由排列成行的数字0-9组成来描述图片，例如：

        image = Image("90009:"
                      "09090:"
                      "00900:"
                      "09090:"
                      "90009")

    will create a 5脳5 image of an X. The end of a line is indicated by a colon.
    It's also possible to use a newline (\n) to indicate the end of a line
    like this::

    上面的函数将创建字符X的5×5图像。描述图片的每一行数字串的结尾用冒号表示， 也可以使用换行符（\n）来表示这样一行的结尾：

        image = Image("90009\n"
                      "09090\n"
                      "00900\n"
                      "09090\n"
                      "90009")

    The other form creates an empty image with ``width`` columns and
    ``height`` rows. Optionally ``buffer`` can be an array of
    ``width``脳``height`` integers in range 0-9 to initialize the image::

    另一种形式是创建一个width列和height行的空图片。 可选的缓冲区可以是宽度×高度在0-9范围的整数数组，用于初始化图像：

        Image(2, 2, b'\x08\x08\x08\x08')

    or::

    	Image(2, 2, bytearray([9,9,9,9]))

    Will create a 2 x 2 pixel image at full brightness.

    将创建全亮度的2 x 2像素的图片。

    .. note::

    注意：

        Keyword arguments cannot be passed to ``buffer``.
        关键字参数不能传递给buffer。

    .. py:method:: width()

        Return the number of columns in the image.

        返回图片的列数。


    .. py:method:: height()

        Return the numbers of rows in the image.

        返回图片的行数。


    .. py:method:: set_pixel(x, y, value)

        Set the brightness of the pixel at column ``x`` and row ``y`` to the
        ``value``, which has to be between 0 (dark) and 9 (bright).

        设置X行Y列像素的亮度值给value，值的范围0（黑）-9（最亮）。

        This method will raise an exception when called on any of the built-in
        read-only images, like ``Image.HEART``.

        当调用任何内置只读图片（如Image.HEART）时，此方法将引发异常。


    .. py:method:: get_pixel(x, y)

        Return the brightness of pixel at column ``x`` and row ``y`` as an
        integer between 0 and 9.

        返回X行Y列的像素的亮度，范围为0-9的整数。


    .. py:method:: shift_left(n)

        Return a new image created by shifting the picture left by ``n``
        columns.

        返回将图片左移n列而得到的新图片。


    .. py:method:: shift_right(n)

        Same as ``image.shift_left(-n)``.

        与image.shift_left(-n)相同。

    .. py:method:: shift_up(n)

        Return a new image created by shifting the picture up by ``n`` rows.

        返回将图片向上移动n行得到的新图片。


    .. py:method:: shift_down(n)

        Same as ``image.shift_up(-n)``.

        与image.shift_up(-n)相同。

    .. py:method:: crop(x, y, w, h)

        Return a new image by cropping the picture to a width of ``w`` and a
	height of ``h``, starting with the pixel at column ``x`` and row ``y``.

        返回从x列和y行的像素开始，将图片裁剪为宽度为w和高度为h的新图片。

    .. py:method:: copy()

        Return an exact copy of the image.

        返回图片的拷贝

    .. py:method:: invert()

        Return a new image by inverting the brightness of the pixels in the
        source image.

        通过反转源图片中像素的亮度来返回新图片。

    .. py:method:: fill(value)

        Set the brightness of all the pixels in the image to the
        ``value``, which has to be between 0 (dark) and 9 (bright).

        设置图片中所有像素的亮度值value，该值的取值范围0（黑）- 9（最亮）。

        This method will raise an exception when called on any of the built-in
        read-only images, like ``Image.HEART``.

        当调用内建只读图片时，这个方法会产生异常，如调用Image.HEART。

    .. py:method:: blit(src, x, y, w, h, xdest=0, ydest=0)

        Copy the rectangle defined by ``x``, ``y``, ``w``, ``h`` from the image ``src`` into
        this image at ``xdest``, ``ydest``.
        Areas in the source rectangle, but outside the source image are treated as having a value of 0.

        将由x、y、w、h定义的矩形从源图片复制到坐标（xdest，ydest）处。在源矩形中但
        超出源图片的部分被视为0。

        ``shift_left()``, ``shift_right()``, ``shift_up()``, ``shift_down()`` and ``crop()``
        can are all implemented by using ``blit()``.
        For example, img.crop(x, y, w, h) can be implemented as::

        shift_left（），shift_right（），shift_up（），shift_down（）和crop（）都可以使用blit（）实现。 例如，img.crop（x，y，w，h）可以实现为：

            def crop(self, x, y, w, h):
                res = Image(w, h)
                res.blit(self, x, y, w, h)
                return res


Attributes 属性
==========

The ``Image`` class also has the following built-in instances of itself
included as its attributes (the attribute names indicate what the image
represents):

Image类还包含以下内置的实例作为其属性（属性名称表示图片代表的内容）：

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

Finally, related collections of images have been grouped together::

最后，相关的图片被组合在一起：

    * ``Image.ALL_CLOCKS``
    * ``Image.ALL_ARROWS``


Operations 操作
==========

.. code::

    repr(image)

Get a compact string representation of the image.

获取图片的压缩字符串表示形式。

.. code::

    str(image)

Get a readable string representation of the image.

获取图片的可读写字符串表示形式。

.. code::

    image1 + image2

Create a new image by adding the brightness values from the two images for
each pixel.

通过两个图片的每个像素亮度值相加来创建新图片。

.. code::

    image * n

Create a new image by multiplying the brightness of each pixel by ``n``.

通过将每个像素的亮度乘以n来创建新图片。
