Audio 音频
*******

.. py:module:: audio

This module allows you play sounds from a speaker attached to the Microbit.
In order to use the audio module you will need to provide a sound source.

这个模块允许你通过接到Microbit上的扬声器发声。为了使用音频模块你必须提供一个声源。

A sound source is an iterable (sequence, like list or tuple, or a generator) of
frames, each of 32 samples.
The ``audio`` modules plays samples at the rate of 7812.5 samples per second,
which means that it can reproduce frequencies up to 3.9kHz.

声源是一个可重复的帧（序列，如列表、数组、生成器），每个帧有32个样本。音频模块以每秒7812.5个样本的速度播放样本，这意味着它可以重现高达3.9kHz的频率。

Functions 函数
=========

.. py:function:: play(source, wait=True, pin=pin0, return_pin=None)

    Play the source to completion.

    完成音频源的播放。

    ``source`` is an iterable, each element of which must be an ``AudioFrame``.

    source是可重复的，其中每个单元必须是一个AudioFrame。

    If ``wait`` is ``True``, this function will block until the source is exhausted.

    如果wait为true，则此函数将阻塞，直到源播放完。

    ``pin`` specifies which pin the speaker is connected to.

    pin指定扬声器连接的引脚。

    ``return_pin`` specifies a differential pin to connect to the speaker
    instead of ground.

    return_pin指定连接扬声器的另一个引脚。而不是接地。

Classes 类
=======

.. py:class::
    AudioFrame

    An ``AudioFrame`` object is a list of 32 samples each of which is a signed byte
    (whole number between -128 and 127).

    AudioFrame对象是32个样本的列表，每个样本都是一个带符号的字节（数值在-128到127之间）。

    It takes just over 4 ms to play a single frame.

    单帧播放只需4毫秒。

Using audio 使用音频
===========

You will need a sound source, as input to the ``play`` function. You can generate your own, like in
``examples/waveforms.py`` or you can use the sound sources provided by modules like ``synth``.

您将需要一个音源作为play函数的输入。您可以生成自己的，如examples/waveforms.py中的，
也可以使用synth等模块提供的音源。


Technical Details 技术细节
=================

.. note::

注意：
    You don't need to understand this section to use the ``audio`` module.
    It is just here in case you wanted to know how it works.

    使用音频模块不需要理解本节内容。在这里只是让你知道它是如何工作的。

The ``audio`` module consumes samples at 7812.5 kHz, and uses linear interpolation to
output a PWM signal at 32.5 kHz, which gives tolerable sound quality.

音频模块以7812.5 kHz的频率采样，并使用线性插值法输出32.5 kHz的PWM信号，从而提供可接受的音质。

The function ``play`` fully copies all data from each ``AudioFrame`` before it
calls ``next()`` for the next frame, so a sound source can use the same ``AudioFrame``
repeatedly.

函数播放在为下一帧调用next（）之前完全复制每个AudioFrame的所有数据，因此声源可以重复使用相同的AudioFrame。

The ``audio`` module has an internal 64 sample buffer from which it reads samples.
When reading reaches the start or the mid-point of the buffer, it triggers a callback to
fetch the next ``AudioFrame`` which is then copied into the buffer.
This means that a sound source has under 4ms to compute the next ``AudioFrame``,
and for reliable operation needs to take less 2ms (which is 32000 cycles, so should be plenty).

音频模块有一个内部64采样缓冲区，从中读取采样。当读取到达缓冲区的起点或中间点时，它会触发回调以获取下一个音频帧，然后将其复制到缓冲区中。这意味着一个声源在4ms以下可以计算下一个音频帧，而可靠的操作需要不到2ms（即32000个周期，所以应该足够）。


Example
=======

.. include:: ../examples/waveforms.py
    :code: python
