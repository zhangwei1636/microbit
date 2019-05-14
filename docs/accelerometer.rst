Accelerometer
*************

.. py:module:: microbit.accelerometer

This object gives you access to the on-board accelerometer. The accelerometer
also provides convenience functions for detecting gestures. The
recognised gestures are: ``up``, ``down``, ``left``, ``right``, ``face up``,
``face down``, ``freefall``, ``3g``, ``6g``, ``8g``, ``shake``.

�������������ʰ��ϵļ��ٶȼơ����ٶȼƻ��ṩ�˱����ĺ���������ơ���ʶ��������У�``up``, ``down``, ``left``, ``right``, ``face up``,
``face down``, ``freefall``, ``3g``, ``6g``, ``8g``, ``shake``.

By default MicroPython sets the accelerometer range to +/- 2g, changing the
accelerometer range is currently not possible in MicroPython.
The accelerometer returns a value in the range 0..1024 for each axis, which is
then scaled accordingly.

Ĭ������£�Micropython�����ٶȼƷ�Χ����Ϊ+/-2g��Ŀǰ�޷���Micropython�и��ļ��ٶȼƷ�Χ�����ٶȼ�Ϊÿ���᷵��һ��0��1024��Χ�ڵ�ֵ��Ȼ����Ӧ�����Ÿ�ֵ��



Functions ����
=========

.. py:function:: get_x()

    Get the acceleration measurement in the ``x`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    ���ݷ���������������������ʽ��ȡx���ϵļ��ٶȲ���ֵ������ֵ��mgΪ��λ��Ĭ��
    ����£����ٶȼƵ����÷�ΧΪ+/-2g����˸÷��������ص�+/-2000mg�ķ�Χ�ڡ�

.. py:function:: get_y()

    Get the acceleration measurement in the ``y`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    ���ݷ���������������������ʽ��ȡy���ϵļ��ٶȲ���ֵ������ֵ��mgΪ��λ��Ĭ��
    ����£����ٶȼƵ����÷�ΧΪ+/-2g����˸÷��������ص�+/-2000mg�ķ�Χ�ڡ�

.. py:function:: get_z()

    Get the acceleration measurement in the ``z`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

    ���ݷ���������������������ʽ��ȡz���ϵļ��ٶȲ���ֵ������ֵ��mgΪ��λ��Ĭ��
    ����£����ٶȼƵ����÷�ΧΪ+/-2g����˸÷��������ص�+/-2000mg�ķ�Χ�ڡ�

.. py:function:: get_values()

    Get the acceleration measurements in all axes at once, as a three-element
    tuple of integers ordered as X, Y, Z.
    By default the accelerometer is configured with a range of +/- 2g, and so
    X, Y, and Z will be within the range of +/-2000mg.

    һ�λ�ȡ�������ϵļ��ٶȲ���ֵ����Ϊһ����Ԫ���������飬Ԫ��˳��Ϊx��y��z��Ĭ��
    ����£����ٶȼƵ����÷�ΧΪ+/-2g�����x��y��z����+/-2000mg��Χ��ȡֵ��

.. py:function:: current_gesture()

    Return the name of the current gesture.

    ���ص�ǰ���Ƶ����ơ�

.. note::
ע�⣺

    MicroPython understands the following gesture names: ``"up"``, ``"down"``,
    ``"left"``, ``"right"``, ``"face up"``, ``"face down"``, ``"freefall"``,
    ``"3g"``, ``"6g"``, ``"8g"``, ``"shake"``. Gestures are always
    represented as strings.

  Micropythonʶ�������������ƣ������ϡ��������¡������󡱡����ҡ������泯�ϡ������泯�¡������������塱����3g������6g������8g�������𶯡��������������ַ�����ʾ��

.. py:function:: is_gesture(name)

    Return True or False to indicate if the named gesture is currently active.

    ����True��False����ʾ��ǰ�����������Ƿ񼤻

.. py:function:: was_gesture(name)

    Return True or False to indicate if the named gesture was active since the
    last call.

    ����True��False�Ա�ʾ���ϴε����������������Ƿ��ڻ״̬��

.. py:function:: get_gestures()

    Return a tuple of the gesture history. The most recent is listed last.
    Also clears the gesture history before returning.

    ����������ʷ�����顣�����������󡣲����ڷ���ǰ���������ʷ��¼��

.. note::

ע�⣺

    Gestures are not updated in the background so there needs to be constant
    calls to some accelerometer method to do the gesture detection. Usually
    gestures can be detected using a loop with a small :func:`microbit.sleep` delay.

    ���Ʋ����ں�̨���£������Ҫ���ϵ���ĳЩ���ٶȼƷ������������Ƽ�⡣ͨ��������
    ����ͨ��microbit.sleep�����ӳٽ϶̵�ѭ������⡣

Examples ����
--------

A fortune telling magic 8-ball. Ask a question then shake the device for an
answer.

����ħ��8�� �������Ȼ��ҡ���豸�Ի�ô𰸡�

.. include:: ../examples/magic8.py
    :code: python

Simple Slalom. Move the device to avoid the obstacles.

�򵥵��ϰ������ƶ��豸�ܿ��ϰ��

.. include:: ../examples/simple_slalom.py
    :code: python
