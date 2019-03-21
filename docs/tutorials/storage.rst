Storage
-------

Sometimes you need to store useful information. Such information is stored as
data: representation of information (in a digital form when stored on
computers). If you store data on a computer it should persist, even if you
switch the device off and on again.

有时你需要存储有用的信息。这些信息存储为数据：信息的表示形式（数据是以数字的形式存储在计算机上）。如果您将数据存储在计算机上，即使开关计算机，数据也会保持不变。

Happily MicroPython on the micro:bit allows you to do this with a very simple
file system. Because of memory constraints **there is approximately 30k of
storage available** on the file system.

令人高兴的是，Micro:bit上的Microython允许您使用一个非常简单的文件系统来完成这项工作。由于内存限制，文件系统上有大约30K的可用存储空间。

.. note::

注意：

    The micropython file system should not be confused
    with the micro:bit mass storage mode which presents the device as a USB drive.
    Mass storage mode is only intended for copying across a HEX file, so you won't
    see files you create using the file system appearing on the MICROBIT drive.

    Micropython文件系统不应与Micro:bit大容量存储模式混淆，后者设备类似于USB驱动器。
    大容量存储模式仅用于存储十六进制文件，因此您不会看到使用文件系统创建的文件出
    现在Microbit驱动器上。

What is a file system?

文件系统是什么？

It's a means of storing and organising data in a persistent manner - any data
stored in a file system should survive restarts of the device. As the name
suggests, data stored on a file system is organised into files.

它是一种以持久的方式存储和组织数据的方法——任何存储在文件系统中的数据都应该在设备重新启动后仍然存在。顾名思义，存储在文件系统中的数据是以文件的形式在。

.. image:: files.jpg

A computer file is a named digital resource that's stored on a file system.
Such resources contain useful information as data. This is exactly how a
paper file works. It's a sort of named container that contains useful
information. Usually, both paper and digital files are named to indicate what
they contain. On computers it is common to end a file with a ``.something``
suffix. Usually, the "something" indicates what type of data is used to
represent the information. For example, ``.txt`` indicates a text file,
``.jpg`` a JPEG image and ``.mp3`` sound data encoded as MP3.

计算机文件是存储在文件系统中的有名字的数字资源。这些资源包含有用的数据信息。跟纸质文件一样。它是一种包含有用信息的命了名的容器。通常，纸张和数字文件的命名都与文件的内容相关。在计算机上，通常以.something后缀为文件的扩展名。通常，“something”用来表示文件的数据类型。例如，.txt表示文本文件，.jpg表示jpeg图像，.mp3表示编码为mp3的声音数据。

Some file systems (such as the one found on your laptop or PC) allow you to
organise your files into directories: named containers that group related files
and sub-directories together. However, *the file system provided by MicroPython
is a flat file system*. A flat file system does not have directories - all
your files are just stored in the same place.

有些文件系统（如笔记本电脑或PC上的文件系统）允许您将文件组织到目录中：将相关文件和子目录组合在一起。但是，Micropython提供的文件系统是一个平面文件系统。平面文件系统没有目录，所有文件都存储在同一个位置。

The Python programming language contains easy to use and powerful ways in which
to work with a computer's file system. MicroPython on the micro:bit implements
a useful subset of these features to make it easy to read and write files on
the device, while also providing consistency with other versions of Python.

python编程语言包含易用而强大的方法来使用计算机文件系统。micro:bit上的Micropython实现了这些功能的一个有用的子集，以使在设备上读取和写入文件变得容易，同时还提供与其他版本python的一致性。

.. warning::

警告：

    Flashing your micro:bit will DESTROY ALL YOUR DATA since it re-writes all
    the flash memory used by the device and the file system is stored in the
    flash memory.

    刷新micro:bit将破坏所有数据，因为它重写设备使用的所有闪存。文件系统是存储在闪存中。

    However, if you switch off your device the data will remain intact until
    you either delete it or re-flash the device.

    但是，如果您关闭设备，存储的数据将保持不变，直到您删除或重新刷新设备。

Open Sesame
+++++++++++

Reading and writing a file on the file system is achieved by the ``open``
function. Once a file is opened you can do stuff with it until you close it
(analogous with the way we use paper files). It is essential you close a file
so MicroPython knows you've finished with it.

在文件系统上读写文件是通过open函数实现的。一旦一个文件被打开，你可以用它做一些事情直到你关闭它（类似于我们使用纸质文件的方式）。文件关闭是必须的，这样Micropython才知道你已经处理完了。

The best way to make sure of this is to use the ``with`` statement like this::

确保这一点的最佳方法是使用如下WITH语句：

    with open('story.txt') as my_file:
        content = my_file.read()
    print(content)

The ``with`` statement uses the ``open`` function to open a file and assign it
to an object. In the example above, the ``open`` function opens the file called
``story.txt`` (obviously a text file containing a story of some sort).
The object that's used to represent the file in the Python code is called
``my_file``. Subsequently, in the code block indented underneath the ``with``
statement, the ``my_file`` object is used to ``read()`` the content of the
file and assign it to the ``content`` object.

with语句使用open函数打开文件并将其分配给对象。 在上面的示例中，open函数打开名为story.txt的文件（显然是包含某种故事的文本文件）。 用于在Python代码中表示文件的对象称为my_file。 随后，在with语句下面缩进的代码块中，my_file对象的read（）方法读取story.txt文件的内容并将其赋给content对象。

Here's the important point, *the next line containing the* ``print`` *statement
is not indented*. The code block associated with the ``with`` statement is only
the single line that reads the file. Once the code block associated with the
``with`` statement is closed then Python (and MicroPython) will automatically
close the file for you. This is called context handling and the ``open``
function creates objects that are context handlers for files.

这里有一点很重要，包含print语句的下一行没有缩进。与WITH语句关联的读取文件的代码块只有一行。一旦与with语句关联的代码块关闭，那么python（和micropython）将自动关闭该文件。这称为上下文处理，open函数创建的对象是文件的上下文处理程序。

Put simply, the scope of your interaction with a file is defined by the code
block associated with the ``with`` statement that opens the file.

简而言之，与文件交互的范围由与打开文件的with语句关联的代码块定义。

Confused?

困惑吗？

Don't be. I'm simply saying your code should look like this::

不要这样。 我只是说你的代码应该是这样的：

    with open('some_file') as some_object:
        # Do stuff with some_object in this block of code
        # associated with the with statement.

    # When the block is finished then MicroPython
    # automatically closes the file for you.

Just like a paper file, a digital file is opened for two reasons: to read its
content (as demonstrated above) or to write something to the file. The default
mode is to read the file. If you want to write to a file you need to tell the
``open`` function in the following way::

与纸质文件一样，打开数字文件有两个原因：读取其内容（如上所示）或向文件写入内容。默认模式是读取文件。如果要写入文件，需要按以下方式告诉open函数：

    with open('hello.txt', 'w') as my_file:
        my_file.write("Hello, World!")

Notice the ``'w'`` argument is used to set the ``my_file`` object into write
mode. You could also pass an ``'r'`` argument to set the file object to read
mode, but since this is the default, it's often left off.

请注意，'w'参数用于将my_file对象设置为写入模式。 您还可以传递一个'r'参数来将文件对象设置为读取模式，但由于这是默认值，因此通常不写。

Writing data to the file is done with the (you guessed it) ``write``
method that takes the string you want to write to the file as an argument. In
the example above, I write the text "Hello, World!" to a file called
"hello.txt".

将数据写入文件是通过（您猜对了）write方法完成的，该方法是将要写入文件的字符串作为参数。 在上面的示例中，将文本“Hello，World！”写入“hello.txt”的文件中。

Simple!

简单！

.. note::

注意：

    When you open a file and write (perhaps several times while the file is
    in an open state) you will be writing OVER the content of the file if it
    already exists.

    当您打开一个文件并进行写入（可能在文件打开多次）时，如果该文件已经存在，将对其
    内容进行覆盖。

    If you want to append data to a file you should first read it, store the
    content somewhere, close it, append your data to the content and then open
    it to write again with the revised content.

    如果要将数据附加到文件中，应首先读取该文件，将内容存储在某个地方，关闭该文件，将
    数据附加到内容中，然后打开该文件使用修改后的内容重新写入。

    While this is the case in MicroPython, "normal" Python can open
    files to write in "append" mode. That we can't do this on the micro:bit is
    a result of the simple implementation of the file system.

    虽然在MicroPython中是这样，但一般Python可以打开文件以“append”模式写入。 我们不
    能在micro：bit上执行此操作是文件系统的简单实现的结果。

OS SOS
++++++

As well as reading and writing files, Python can manipulate them. You
certainly need to know what files are on the file system and sometimes
you need to delete them too.

除了读写文件外，Python还可以操作它们。 当然需要知道文件系统中有哪些文件，有时也需要删除它们。

On a regular computer, it is the role of the operating system (like Windows,
OSX or Linux) to manage this on Python's behalf. Such functionality is made
available in Python via a module called ``os``. Since MicroPython **is** the
operating system we've decided to keep the appropriate functions in the ``os``
module for consistency so you'll know where to find them when you use "regular"
Python on a device like a laptop or Raspberry Pi.

在普通计算机上，操作系统（如Windows、OSX或Linux）的作用是在python的支持下来管理它。这种功能通过Python中的一个叫作OS的模块起作用。由于Micropython是操作系统，决定在操作系统模块中保留适当的功能以保持一致性，这样当您在笔记本电脑或树莓PI等设备上使用python时，您就知道在哪里可以找到它们。

Essentially, you can do three operations related to the file system: list the
files, remove a file and ask for the size of a file.

基本上，您可以执行与文件系统相关的三个操作：列出文件、删除文件和询问文件大小。

To list the files on your file system use the ``listdir`` function. It
returns a list of strings indicating the file names of the files on the file
system::

要列出文件系统上的文件，请使用listdir函数。 它返回一个字符串列表，指示文件系统上文件的文件名：

    import os
    my_files = os.listdir()

To delete a file use the ``remove`` function. It takes a string representing
the file name of the file you want to delete as an argument, like this::

要删除文件，使用remove函数。它将一个想要删除文件的文件名字符串作为参数，如下所示：

    import os
    os.remove('filename.txt')

Finally, sometimes it's useful to know how big a file is before reading from
it. To achieve this use the ``size`` function. Like the ``remove`` function, it
takes a string representing the file name of the file whose size you want to
know. It returns an integer (whole number) telling you the number of bytes the
file takes up::

最后，有时在读取文件之前知道它有多大是很有用的。使用size函数读取文件的大小。与remove函数类似，使用想知道其大小的文件名字符串作为参数。它返回一个整数，告诉您文件占用的字节数：

    import os
    file_size = os.size('a_big_file.txt')

It's all very well having a file system, but what if we want to put or get
files on or off the device?

拥有文件系统非常好，但是如果我们想要在设备上放置或取出文件怎么办？

Just use the ``microfs`` utility!

只需使用microfs实用程序！

File Transfer
+++++++++++++

If you have Python installed on the computer you use to program your BBC
micro:bit then you can use a special utility called ``microfs`` (shortened to
``ufs`` when using it in the command line). Full instructions for installing
and using all the features of microfs can be found
`in its documentation <https://microfs.readthedocs.io>`_.

如果你在计算机上安装了Python来为BBC micro：bit编程，那么你可以使用一个名为microfs的特殊工具（在命令行中使用它时缩短为ufs）。 有关安装和使用microfs所有功能的完整说明，请参阅其文档。

Nevertheless it's possible to do most of the things you need with just four
simple commands::

不过，只需四个简单的命令就可以完成大部分工作：

    $ ufs ls
    story.txt

The ``ls`` sub-command lists the files on the file system (it's named after
the common Unix command, ``ls``, that serves the same function).

ls子命令列出文件系统上的文件（它与普通的Unix命令ls一样命名，它提供相同的功能）。

::

    $ ufs get story.txt

The ``get`` sub-command gets a file from the connected micro:bit and saves it
into your current location on your computer (it's named after the ``get``
command that's part of the common file transfer protocol [FTP] that serves the
same function).

get子命令从连接的micro:bit中获取一个文件，并将其保存到计算机上的当前位置（它与通用文件传输协议[ftp]的get命令具有相同的功能）。

::

    $ ufs rm story.txt

The ``rm`` sub-command removes the named file from the file system on the
connected micro:bit (it's named after the common Unix command, ``rm``, that
serves the same function).

rm子命令从连接的micro：bit上的文件系统中删除命名文件（它以Unix的rm命令命名，提供相同的功能）。

::

    $ ufs put story2.txt

Finally, the ``put`` sub-command puts a file from your computer onto the
connected device (it's named after the ``put`` command that's part of FTP that
serves the same function).

最后，put子命令将一个文件从您的计算机输入连接的设备（它以put命令命名，与FTP中的一部分功能相同）。

Mainly main.py
++++++++++++++

The file system also has an interesting property: if you just flashed the
MicroPython runtime onto the device then when it starts it's simply waiting
for something to do. However, if you copy a special file called ``main.py``
onto the file system, upon restarting the device, MicroPython will run the
contents of the ``main.py`` file.

文件系统也有一个有趣的特性：如果只是在设备上刷新了MicroPython运行时，那么当它启动时，它只是在等待做些什么。但是，如果将名为main.py的特殊文件复制到文件系统中，重新启动设备后，Micropyhon将运行main.py文件的内容。

Furthermore, if you copy other Python files onto the file system then you can
``import`` them as you would any other Python module. For example, if you had
a ``hello.py`` file that contained the following simple code::

此外，如果您将其他python文件复制到文件系统中，那么您可以像导入任何其他python模块一样导入它们。例如，如果您有一个hello.py文件，其中包含以下简单代码：

    def say_hello(name="World"):
        return "Hello, {}!".format(name)

...you could import and use the ``say_hello`` function like this::

...你可以像这样导入和使用say_hello函数：

    from microbit import display
    from hello import say_hello

    display.scroll(say_hello())

Of course, it results in the text "Hello, World!" scrolling across the
display. The important point is that such an example is split between two
Python modules and the ``import`` statement is used to share code.

当然，它会导致文本“你好，世界！“在显示屏上滚动。重要的一点是，这样一个示例在两个python模块之间拆分，import语句用于共享代码。

.. note::

注意：
    If you have flashed a script onto the device in addition to the MicroPython
    runtime, then MicroPython will ignore ``main.py`` and run your embedded
    script instead.

    如果除了MicroPython运行时外，您将脚本刷新到设备上，那么Micropyhon将忽略main.py
    而运行嵌入的脚本。

    To flash just the MicroPython runtime, simply make sure the script you
    may have written in your editor has zero characters in it. Once flashed
    you'll be able to copy over a ``main.py`` file.

    要只刷新Micropython运行时，只需确保在编辑器中编写一个空脚本。一旦刷新，你将能够
    复制一个main.py文件。

.. footer:: The image of paper files is used under a Creative Commons License and is available here: https://www.flickr.com/photos/jenkim/2270085025
