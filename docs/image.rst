Image ͼƬ
*****

.. py:module:: microbit

The ``Image`` class is used to create images that can be displayed easily on
the device's LED matrix. Given an image object it's possible to display it via
the ``display`` API::

Image�����ڴ��������豸��LED������������ʾ��ͼƬ������ͼ����󣬿���ͨ��display API��ʾ����

    display.show(Image.HAPPY)

.. image:: image-smile.png

There are four ways in which you can construct an image:

�����ַ������Թ���ͼƬ��

- ``Image()`` - Create a blank 5x5 image

-Image() - ����һ��5X5�Ŀհ�ͼƬ

- ``Image(string)`` - Create an image by parsing the string, a single character
  returns that glyph

-Image(string) - ͨ�������ַ���������ͼƬ�������ַ����ظ�����

- ``Image(width, height)`` - Create a blank image of given size

-Image(width, height) - ����ָ����С��ͼƬ

- ``Image(width, height, buffer)`` - Create an image from the given buffer

-Image(width, height, buffer) - �Ӹ�������������ͼƬ


Classes ��
=======

.. py:class::
    Image(string)
    Image(width=None, height=None, buffer=None)

    If ``string`` is used, it has to consist of digits 0-9 arranged into
    lines, describing the image, for example::

    ���ʹ���ַ���������������г��е�����0-9���������ͼƬ�����磺

        image = Image("90009:"
                      "09090:"
                      "00900:"
                      "09090:"
                      "90009")

    will create a 5×5 image of an X. The end of a line is indicated by a colon.
    It's also possible to use a newline (\n) to indicate the end of a line
    like this::

    ����ĺ����������ַ�X��5��5ͼ������ͼƬ��ÿһ�����ִ��Ľ�β��ð�ű�ʾ�� Ҳ����ʹ�û��з���\n������ʾ����һ�еĽ�β��

        image = Image("90009\n"
                      "09090\n"
                      "00900\n"
                      "09090\n"
                      "90009")

    The other form creates an empty image with ``width`` columns and
    ``height`` rows. Optionally ``buffer`` can be an array of
    ``width``×``height`` integers in range 0-9 to initialize the image::

    ��һ����ʽ�Ǵ���һ��width�к�height�еĿ�ͼƬ�� ��ѡ�Ļ����������ǿ�ȡ��߶���0-9��Χ���������飬���ڳ�ʼ��ͼ��

        Image(2, 2, b'\x08\x08\x08\x08')

    or::

    	Image(2, 2, bytearray([9,9,9,9]))

    Will create a 2 x 2 pixel image at full brightness.

    ������ȫ���ȵ�2 x 2���ص�ͼƬ��

    .. note::

    ע�⣺

        Keyword arguments cannot be passed to ``buffer``.
        �ؼ��ֲ������ܴ��ݸ�buffer��

    .. py:method:: width()

        Return the number of columns in the image.

        ����ͼƬ��������


    .. py:method:: height()

        Return the numbers of rows in the image.

        ����ͼƬ��������


    .. py:method:: set_pixel(x, y, value)

        Set the brightness of the pixel at column ``x`` and row ``y`` to the
        ``value``, which has to be between 0 (dark) and 9 (bright).

        ����X��Y�����ص�����ֵ��value��ֵ�ķ�Χ0���ڣ�-9����������

        This method will raise an exception when called on any of the built-in
        read-only images, like ``Image.HEART``.

        �������κ�����ֻ��ͼƬ����Image.HEART��ʱ���˷����������쳣��


    .. py:method:: get_pixel(x, y)

        Return the brightness of pixel at column ``x`` and row ``y`` as an
        integer between 0 and 9.

        ����X��Y�е����ص����ȣ���ΧΪ0-9��������


    .. py:method:: shift_left(n)

        Return a new image created by shifting the picture left by ``n``
        columns.

        ���ؽ�ͼƬ����n�ж��õ�����ͼƬ��


    .. py:method:: shift_right(n)

        Same as ``image.shift_left(-n)``.

        ��image.shift_left(-n)��ͬ��

    .. py:method:: shift_up(n)

        Return a new image created by shifting the picture up by ``n`` rows.

        ���ؽ�ͼƬ�����ƶ�n�еõ�����ͼƬ��


    .. py:method:: shift_down(n)

        Same as ``image.shift_up(-n)``.

        ��image.shift_up(-n)��ͬ��

    .. py:method:: crop(x, y, w, h)

        Return a new image by cropping the picture to a width of ``w`` and a
	height of ``h``, starting with the pixel at column ``x`` and row ``y``.

        ���ش�x�к�y�е����ؿ�ʼ����ͼƬ�ü�Ϊ���Ϊw�͸߶�Ϊh����ͼƬ��

    .. py:method:: copy()

        Return an exact copy of the image.

        ����ͼƬ�Ŀ���

    .. py:method:: invert()

        Return a new image by inverting the brightness of the pixels in the
        source image.

        ͨ����תԴͼƬ�����ص�������������ͼƬ��

    .. py:method:: fill(value)

        Set the brightness of all the pixels in the image to the
        ``value``, which has to be between 0 (dark) and 9 (bright).

        ����ͼƬ���������ص�����ֵvalue����ֵ��ȡֵ��Χ0���ڣ�- 9����������

        This method will raise an exception when called on any of the built-in
        read-only images, like ``Image.HEART``.

        �������ڽ�ֻ��ͼƬʱ���������������쳣�������Image.HEART��

    .. py:method:: blit(src, x, y, w, h, xdest=0, ydest=0)

        Copy the rectangle defined by ``x``, ``y``, ``w``, ``h`` from the image ``src`` into
        this image at ``xdest``, ``ydest``.
        Areas in the source rectangle, but outside the source image are treated as having a value of 0.

        ����x��y��w��h����ľ��δ�ԴͼƬ���Ƶ����꣨xdest��ydest��������Դ�����е�
        ����ԴͼƬ�Ĳ��ֱ���Ϊ0��

        ``shift_left()``, ``shift_right()``, ``shift_up()``, ``shift_down()`` and ``crop()``
        can are all implemented by using ``blit()``.
        For example, img.crop(x, y, w, h) can be implemented as::

        shift_left������shift_right������shift_up������shift_down������crop����������ʹ��blit����ʵ�֡� ���磬img.crop��x��y��w��h������ʵ��Ϊ��

            def crop(self, x, y, w, h):
                res = Image(w, h)
                res.blit(self, x, y, w, h)
                return res


Attributes ����
==========

The ``Image`` class also has the following built-in instances of itself
included as its attributes (the attribute names indicate what the image
represents):

Image�໹�����������õ�ʵ����Ϊ�����ԣ��������Ʊ�ʾͼƬ��������ݣ���

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

�����ص�ͼƬ�������һ��

    * ``Image.ALL_CLOCKS``
    * ``Image.ALL_ARROWS``


Operations ����
==========

.. code::

    repr(image)

Get a compact string representation of the image.

��ȡͼƬ��ѹ���ַ�����ʾ��ʽ��

.. code::

    str(image)

Get a readable string representation of the image.

��ȡͼƬ�Ŀɶ�д�ַ�����ʾ��ʽ��

.. code::

    image1 + image2

Create a new image by adding the brightness values from the two images for
each pixel.

ͨ������ͼƬ��ÿ����������ֵ�����������ͼƬ��

.. code::

    image * n

Create a new image by multiplying the brightness of each pixel by ``n``.

ͨ����ÿ�����ص����ȳ���n��������ͼƬ��
