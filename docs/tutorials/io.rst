Input/Output
------------

There are strips of metal along the bottom edge of the BBC micro:bit that make
it look as if the device has teeth. These are the input/output pins (or I/O pins
for short).

BBC micro��bit�ĵױ��н��������������������ݡ� ��Щ������/������ţ�����I / O���ţ���

.. image:: blue-microbit.png

Some of the pins are bigger than others so it's possible to attach crocodile
clips to them. These are the ones labelled 0, 1, 2, 3V and GND (computers
always start counting from zero). If you attach an edge connector board to the
device it's possible to plug in wires connected to the other (smaller) pins.

��Щ��ű�������Ŵ����Կ��Խ�����������ӵ��������档 ��Щ��ű��Ϊ0,1,2,3V��GND
�������ʼ�մ��㿪ʼ���������������Ե�����������ӵ��豸������Բ������ӵ���������С��
���ŵĵ��ߡ�

Each pin on the BBC micro:bit is represented by an *object* called ``pinN``
where ``N`` is the pin number. So, for example, to do things with the pin
labelled with a 0 (zero), use the object called ``pin0``.

BBC micro��bit�ϵ�ÿ�������ɳ�ΪpinN�Ķ����ʾ������N�����ű�š� ��ˣ�����Ҫ�Ա�
��0���㣩������ִ�в�������ʹ����Ϊpin0�Ķ���

Simple!

These objects have various *methods* associated with them depending upon what
the specific pin is capable of.

��Щ���������֮������ĸ��ַ���������ȡ�����ض��ܽŵĹ��ܡ�

Ticklish Python

+++++++++++++++

��������Python��

The simplest example of input via the pins is a check to see if they are
touched. So, you can tickle your device to make it laugh like this::

������������ʾ���Ǽ�������Ƿ񱻴����� ���ԣ����豸������Ц��

    from microbit import *

    while True:
        if pin0.is_touched():
            display.show(Image.HAPPY)
        else:
            display.show(Image.SAD)

With one hand, hold your device by the GND pin. Then, with your other hand,
touch (or tickle) the 0 (zero) pin. You should see the display change from
grumpy to happy!

��һֻ����סGND���š� Ȼ������һֻ�ִ�������������0���㣩���š� ��Ӧ�ÿ�����
ʾ�ӷ�ŭ��Ϊ���֣�

This is a form of very basic input measurement. However, the fun really starts
when you plug in circuits and other devices via the pins.

����һ�ַǳ����������������ʽ�� Ȼ��������ͨ�����Ž����·�������豸ʱ������
����Ȥ�Ϳ�ʼ�ˡ�

Bleeps and Bloops
+++++++++++++++++

The simplest thing we can attach to the device is a Piezo buzzer. We're going
to use it for output.

���ӵ��豸�ϵ���򵥵Ķ�����Piezo�������� ���ǰ������������

.. image:: piezo_buzzer.jpg

These small devices play a high-pitched bleep when connected to a circuit. To
attach one to your BBC micro:bit you should attach crocodile clips to pin 0 and
GND (as shown below).

�����������ӵ��豸ʱ�ᷢ���������������� ������н����������ӵ�BBC micro��bit��
����0��GND������ͼ��ʾ����

.. image:: pin0-gnd.png

The wire from pin 0 should be attached to the positive connector on the buzzer
and the wire from GND to the negative connector.

����0Ӧ���ӵ��������ϵ�������GND���ӵ�������

The following program will cause the buzzer to make a sound::

���³���ʹ����������������

    from microbit import *

    pin0.write_digital(1)

This is fun for about 5 seconds and then you'll want to make the horrible
squeaking stop. Let's improve our example and make the device bleep::

�����Ȥ����Լ5���ӣ�Ȼ�������Ҫ�ÿ��µ�֨֨��ֹͣ�� �����ǸĽ�ʾ����ʹ�豸������������

    from microbit import *

    while True:
        pin0.write_digital(1)
        sleep(20)
        pin0.write_digital(0)
        sleep(480)

Can you work out how this script works? Remember that ``1`` is "on" and ``0``
is "off" in the digital world.

����Ū�������ű�����ι������� ���ס������������1�ǡ�������0�ǡ��ء���

The device is put into an infinite loop and immediately switches pin 0 on. This
causes the buzzer to emit a beep. While the buzzer is beeping, the device
sleeps for twenty milliseconds and then switches pin 0 off. This gives the
effect of a short bleep. Finally, the device sleeps for 480 milliseconds before
looping back and starting all over again. This means you'll get two bleeps per
second (one every 500 milliseconds).

�����������ѭ����������������0�� ���ʹ������������������ ������������������ʱ���豸������20���룬Ȼ��ر�����0�� ���������ݵ��������� ����豸����ѭ�����ز����¿�ʼ֮ǰ����480���롣 ����ζ����ÿ���õ�������������ÿ500����һ�Σ���

We've made a very simple metronome!

����������һ���ǳ��򵥵Ľ�������

.. footer:: The image of the pizeo buzzer is CC BY-NC-SA 3.0 from https://www.flickr.com/photos/tronixstuff/4821350094
