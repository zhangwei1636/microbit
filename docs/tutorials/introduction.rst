Introduction
------------
介绍

We suggest you download and use the `mu editor <http://codewith.mu/>`_ when
working through these tutorials. Instructions for downloading and installing
Mu are on its website. You may need to install a driver, depending on your
platform (instruction are on the website).

我们建议您使用这些教程时下载并使用mu编辑器。 有关下载和安装Mu的说明，请访问其网站。
您可能需要安装驱动程序，具体取决于您的平台（说明在网站上）。

Mu works with Windows, OSX and Linux.

Mu适用于Windows，OSX和Linux。

Once Mu is installed connect your micro:bit to your computer via a USB lead.

安装Mu后，通过USB线将micro：bit连接到计算机。

Write your script in the editor window and click the "Flash" button to transfer
it to the micro:bit. If it doesn't work, make sure your micro:bit appears as
a USB storage device in your file system explorer.

在编辑器窗口中编写脚本，然后单击“Flash”按钮将其传输到micro:bit。 如果它不起作用，
请确保您的micro:bit在资源管理器中显示为USB存储设备。

.. toctree::
    :maxdepth: 2
    :caption: Tutorials

    hello
    images
    buttons
    io
    music
    random
    movement
    gestures
    direction
    storage
    speech
    network
    radio
    next

Python is one of the `world's most popular <http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html>`_ programming languages. Every day, without
realising, you probably use software written using Python. All sorts of
companies and organisations use Python for a diverse range of applications.
Google, NASA, Bank of America, Disney, CERN, YouTube, Mozilla, The Guardian -
the list goes on and covers all sectors of the economy, science and the arts.

Python是世界上最流行的编程语言之一。 每天，你可能都会无意识地使用Python编写的软件。
 各种公司和组织都将Python用于各种各样的应用程序。 谷歌、美国国家航空航天局、美国银行、
迪士尼、欧洲核子研究中心，YouTube，Mozilla，卫报 - 该名单继续涵盖经济、科学和艺术的所有领域。

For example, do you remember the announcement of the `discovery of gravitational waves <http://www.bbc.co.uk/news/science-environment-35552207>`_? The instruments used to make the measurements were controlled `with Python <https://www.reddit.com/r/IAmA/comments/45g8qu/we_are_the_ligo_scientific_collaboration_and_we/czxnlux>`_.

例如，你还记得发现引力波的消息吗？ 用于进行测量的仪器是由Python控制的。

Put simply, if you teach or learn Python, you are developing a highly valuable
skill that applies to all areas of human endeavour.

简而言之，如果您教授或学习Python，您正在开发一种适用于人类努力的所有领域的高度有价值的技能。

One such area is the BBC's amazing micro:bit device. It runs a version of
Python called MicroPython that's designed to run on small computers like the BBC
micro:bit. It's a full implementation of Python 3 so when you move onto other
things (such as programming Python on a Raspberry Pi) you'll use exactly the
same language.

其中一个领域是BBC令人惊叹的micro：bit设备。 它运行一个名为MicroPython的Python版本，
它被设计为在象BBC micro：bit等小型计算机上运行。 它是Python 3的完整实现，因此当您转移
到其他事物（例如在Raspberry Pi上编程Python）时，您将使用完全相同的语言。

MicroPython does not include all the standard code libraries that come with
"regular" Python. However, we have created a special ``microbit`` module in
MicroPython that lets you control the device.

MicroPython不包含“常规”Python附带的所有标准代码库。 但是，我们在MicroPython中
创建了一个特殊的microbit模块，可以让您控制设备。

Python and MicroPython are free software. Not only does this mean you don't pay
anything to use Python, but you are also free to contribute back to the Python
community. This may be in the form of code, documentation, bug reports, running
a community group or writing tutorials (like this one). In fact, all the Python
related resources for the BBC micro:bit have been created by an international
team of volunteers working in their free time.

Python和MicroPython是免费软件。 这不仅意味着您不需要支付任何费用来使用Python，而且
您也要自由地回馈Python社区。 这可能是代码、文档、错误报告、运行社区组或者编写教程
（如本教程）的形式。 事实上，BBC micro：bit的所有Python相关资源都是由一个国际志愿者
团队在空闲时间创建的。

These lessons introduce MicroPython and the BBC
micro:bit in easy-to-follow steps. Feel free to adopt and adapt them for
classroom based lessons, or perhaps just follow them on your own at home.

这些课程以简单的一步步的步骤介绍MicroPython和BBC micro：bit。 您可以随意采用和调整它们用
于课堂教学，也可以在家中自己一步步地跟着教程学习。

You'll have most success if you explore, experiment and play. You can't break
a BBC micro:bit by writing incorrect code. Just dive in!

如果你进行探索、实验和游戏，你将获得最大的成功。 你不能通过编写错误的代码来破坏BBC micro：bit。尽管操作吧！

A word of warning: *you will fail many times*, and that is fine. **Failure is
how good software developers learn**. Those of us who work as software
developers have a lot of fun tracking down bugs and avoiding the repetition of
mistakes.

一句警告：你会多次失败，那不可怕。失败是软件开发人员学习的好方法。作为软件开发人员，跟踪错误和避免重复错误我们乐在其中。

If in doubt, remember the Zen of MicroPython::

如果有疑问，请记住MicroPython的格言：

    Code,
    Hack it,
    Less is more,
    Keep it simple,
    Small is beautiful,

    Be brave! Break things! Learn and have fun!
    Express yourself with MicroPython.

    Happy hacking! :-)

Best of luck!

         代码，
???? 哈哈，
???? 少即是多，
???? 把事情简单化，
???? 小很美，

???? 勇敢起来！ 打破一切！ 玩着学！
???? 用MicroPython表达自己。

???? 快乐的黑客！

祝你好运！
