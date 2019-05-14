Audio ��Ƶ
*******

.. py:module:: audio

This module allows you play sounds from a speaker attached to the Microbit.
In order to use the audio module you will need to provide a sound source.

���ģ��������ͨ���ӵ�Microbit�ϵ�������������Ϊ��ʹ����Ƶģ��������ṩһ����Դ��

A sound source is an iterable (sequence, like list or tuple, or a generator) of
frames, each of 32 samples.
The ``audio`` modules plays samples at the rate of 7812.5 samples per second,
which means that it can reproduce frequencies up to 3.9kHz.

��Դ��һ�����ظ���֡�����У����б����顢����������ÿ��֡��32����������Ƶģ����ÿ��7812.5���������ٶȲ�������������ζ�����������ָߴ�3.9kHz��Ƶ�ʡ�

Functions ����
=========

.. py:function:: play(source, wait=True, pin=pin0, return_pin=None)

    Play the source to completion.

    �����ƵԴ�Ĳ��š�

    ``source`` is an iterable, each element of which must be an ``AudioFrame``.

    source�ǿ��ظ��ģ�����ÿ����Ԫ������һ��AudioFrame��

    If ``wait`` is ``True``, this function will block until the source is exhausted.

    ���waitΪtrue����˺�����������ֱ��Դ�����ꡣ

    ``pin`` specifies which pin the speaker is connected to.

    pinָ�����������ӵ����š�

    ``return_pin`` specifies a differential pin to connect to the speaker
    instead of ground.

    return_pinָ����������������һ�����š������ǽӵء�

Classes ��
=======

.. py:class::
    AudioFrame

    An ``AudioFrame`` object is a list of 32 samples each of which is a signed byte
    (whole number between -128 and 127).

    AudioFrame������32���������б�ÿ����������һ�������ŵ��ֽڣ���ֵ��-128��127֮�䣩��

    It takes just over 4 ms to play a single frame.

    ��֡����ֻ��4���롣

Using audio ʹ����Ƶ
===========

You will need a sound source, as input to the ``play`` function. You can generate your own, like in
``examples/waveforms.py`` or you can use the sound sources provided by modules like ``synth``.

������Ҫһ����Դ��Ϊplay���������롣�����������Լ��ģ���examples/waveforms.py�еģ�
Ҳ����ʹ��synth��ģ���ṩ����Դ��


Technical Details ����ϸ��
=================

.. note::

ע�⣺
    You don't need to understand this section to use the ``audio`` module.
    It is just here in case you wanted to know how it works.

    ʹ����Ƶģ�鲻��Ҫ��Ȿ�����ݡ�������ֻ������֪��������ι����ġ�

The ``audio`` module consumes samples at 7812.5 kHz, and uses linear interpolation to
output a PWM signal at 32.5 kHz, which gives tolerable sound quality.

��Ƶģ����7812.5 kHz��Ƶ�ʲ�������ʹ�����Բ�ֵ�����32.5 kHz��PWM�źţ��Ӷ��ṩ�ɽ��ܵ����ʡ�

The function ``play`` fully copies all data from each ``AudioFrame`` before it
calls ``next()`` for the next frame, so a sound source can use the same ``AudioFrame``
repeatedly.

����������Ϊ��һ֡����next����֮ǰ��ȫ����ÿ��AudioFrame���������ݣ������Դ�����ظ�ʹ����ͬ��AudioFrame��

The ``audio`` module has an internal 64 sample buffer from which it reads samples.
When reading reaches the start or the mid-point of the buffer, it triggers a callback to
fetch the next ``AudioFrame`` which is then copied into the buffer.
This means that a sound source has under 4ms to compute the next ``AudioFrame``,
and for reliable operation needs to take less 2ms (which is 32000 cycles, so should be plenty).

��Ƶģ����һ���ڲ�64���������������ж�ȡ����������ȡ���ﻺ�����������м��ʱ�����ᴥ���ص��Ի�ȡ��һ����Ƶ֡��Ȼ���临�Ƶ��������С�����ζ��һ����Դ��4ms���¿��Լ�����һ����Ƶ֡�����ɿ��Ĳ�����Ҫ����2ms����32000�����ڣ�����Ӧ���㹻����


Example
=======

.. include:: ../examples/waveforms.py
    :code: python
