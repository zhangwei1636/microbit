Compass ָ����
*******

.. py:module:: microbit.compass

This module lets you access the built-in electronic compass. Before using,
the compass should be calibrated, otherwise the readings may be wrong.

��ģ���������������õ���ָ���롣ʹ��ǰӦУ׼ָ���룬���������������

.. warning::

���棺

    Calibrating the compass will cause your program to pause until calibration
    is complete. Calibration consists of a little game to draw a circle on the
    LED display by rotating the device.

    У׼ָ���뽫���³�����ͣ��ֱ��У׼��ɡ�У׼��ͨ����ת�豸��LED��ʾ���ϻ�һ��Բ��
    С������ɡ�


Functions ����
=========

.. py:function:: calibrate()

    Starts the calibration process. An instructive message will be scrolled
    to the user after which they will need to rotate the device in order to
    draw a circle on the LED display.

    ��ʼУ׼���̡������û�������ʾһ��ָʾ��Ϣ��Ȼ���û���Ҫ��ת�豸���Ա���LED��ʾ
    ���ϻ�һ��ԲȦ��

.. py:function:: is_calibrated()

    Returns ``True`` if the compass has been successfully calibrated, and
    returns ``False`` otherwise.

    ���ָ����У׼�ɹ��򷵻�True�����򷵻�False��


.. py:function:: clear_calibration()

    Undoes the calibration, making the compass uncalibrated again.

    ����У׼��ʹָ���봦��δУ׼��


.. py:function:: get_x()

    Gives the reading of the magnetic field strength on the ``x`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    ���ݴų��ķ���������������������ʽ����x���ϴų�ǿ�ȵĶ�������λΪ����˹����


.. py:function:: get_y()

    Gives the reading of the magnetic field strength on the ``y`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    ���ݴų��ķ���������������������ʽ����y���ϴų�ǿ�ȵĶ�������λΪ����˹����


.. py:function:: get_z()

    Gives the reading of the magnetic field strength on the ``z`` axis in nano
    tesla, as a positive or negative integer, depending on the direction of the
    field.

    ���ݴų��ķ���������������������ʽ����z���ϴų�ǿ�ȵĶ�������λΪ����˹����


.. py:function:: heading()

    Gives the compass heading, calculated from the above readings, as an
    integer in the range from 0 to 360, representing the angle in degrees,
    clockwise, with north as 0.

    ����ָ���뷽�򣬸��������������������0��360֮���������ʾ���Զ�Ϊ��λ�ĽǶȣ�
    ˳ʱ��Ϊ������Ϊ0�ȡ�


.. py:function:: get_field_strength()

    Returns an integer indication of the magnitude of the magnetic field around
    the device in nano tesla.

    �����豸��Χ�ų�ǿ�ȵ�����ֵ����λΪ����˹����


Example ����
=======

.. include:: ../examples/compass.py
    :code: python
