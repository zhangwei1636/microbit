.. BBC Microbit Micropython documentation master file, created by
   sphinx-quickstart on Tue Oct 20 10:41:30 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

BBC micro:bit MicroPython documentation
=======================================

Welcome!
欢迎

The BBC micro:bit is a small computing device for children. One of the
languages it understands is the popular Python programming language. The
version of Python that runs on the BBC micro:bit is called MicroPython.


BBC micro：bit是一款适合儿童使用的小型计算设备。 它所理解的语言之一是流行的Python编程语言。
在BBC micro：bit上运行的Python版本称为MicroPython。

This documentation includes lessons for teachers
and API documentation for developers (check out the index on the left). We hope
you enjoy developing for the BBC micro:bit using MicroPython.

该文档包括教师的课程和开发人员的API文档（查看左侧的索引）。我们希望你喜欢使用MicroPython开发BBC micro：bit。

If you're a new programmer, teacher or unsure where to start, begin with the tutorials.

如果您是新的程序员、老师或不确定从哪里开始，请从教程开始。

.. image:: comic.png

To get involved with the community subscribe to the microbit@python.org
mailing list (https://mail.python.org/mailman/listinfo/microbit).

要加入社区，请订阅microbit@python.org 邮件列表（https://mail.python.org/mailman/listinfo/microbit）。

.. note::

    This project is under active development. Please help other
    developers by adding tips, how-tos, and Q&A to this document.
    Thanks!

.. 注意 ::

    该项目正在积极开发中。 请帮助其他开发人员为此文档添加提示、操作方法和问答。
    谢谢！

Projects related to MicroPython on the BBC micro:bit include:

在BBC micro上与MicroPython相关的项目包括：

* `Mu <https://github.com/ntoll/mu>`_ - a simple code editor for kids, teachers and beginner programmers. Probably the easiest way for people to program MicroPython on the BBC micro:bit.

* Mu - 一个简单的代码编辑器，适用于儿童、教师和初学者程序员。 可能是人们在BBC micro：bit上编MicroPython最简单的方法。

* `uFlash <https://uflash.readthedocs.io/en/latest/>`_ - a command line tool for flashing raw Python scripts onto a BBC micro:bit.

* uFlash - 用于将原生的python脚本刷新到BBC micro:bit上的命令行工具。

.. toctree::
    :maxdepth: 2
    :caption: Tutorials

    tutorials/introduction
    tutorials/hello
    tutorials/images
    tutorials/buttons
    tutorials/io
    tutorials/music
    tutorials/random
    tutorials/movement
    tutorials/gestures
    tutorials/direction
    tutorials/storage
    tutorials/speech
    tutorials/network
    tutorials/radio
    tutorials/next

.. toctree::
   :maxdepth: 2
   :caption: API Reference

   microbit_micropython_api.rst
   microbit.rst
   accelerometer.rst
   audio.rst
   ble.rst
   button.rst
   compass.rst
   display.rst
   filesystem.rst
   i2c.rst
   image.rst
   machine.rst
   micropython.rst
   music.rst
   neopixel.rst
   os.rst
   pin.rst
   radio.rst
   random.rst
   speech.rst
   spi.rst
   uart.rst
   utime.rst

.. toctree::
   :maxdepth: 2
   :caption: Developer Guide

   devguide/installation
   devguide/flashfirmware
   devguide/repl
   devguide/hexformat
   devguide/devfaq
   devguide/contributing

.. toctree::
   :maxdepth: 2
   :caption: Indices and tables

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
