Gestures (����)
--------

The really interesting side-effect of having an accelerometer is gesture
detection. If you move your BBC micro:bit in a certain way (as a gesture) then
MicroPython is able to detect this.

���ٶȼ�������Ȥ�ĸ���������̬��⡣�������ĳ�ַ�ʽ�ƶ����bbc micro:bit���������ƣ�����ômicropython���ܹ���⵽��һ�㡣

MicroPython is able to recognise the following gestures: ``up``, ``down``,
``left``, ``right``, ``face up``, ``face down``, ``freefall``, ``3g``, ``6g``,
``8g``, ``shake``. Gestures are always represented as strings. While most of
the names should be obvious, the ``3g``, ``6g`` and ``8g`` gestures apply when
the device encounters these levels of g-force (like when an astronaut is
launched into space).

MicroPython�ܹ�ʶ���������ƣ��ϣ��£����ң��泯�ϣ��泯�£��������壬3g��6g��8g��ҡ�Ρ� �������Ǳ�ʾΪ�ַ����� ��Ȼ��������ƶ�Ӧ���������Զ��׼��ģ����ǵ��豸�ﵽ��Щg-forceʱ�����統�Ա�����䵽̫��ʱ�����豸����ʾ3g��6g��8g���ơ�

To get the current gesture use the ``accelerometer.current_gesture`` method.
Its result is going to be one of the named gestures listed above. For example,
this program will only make your device happy if it is face up::

Ҫ��ȡ��ǰ���ƣ���ʹ��accelerometer.current_gesture������ ��������ʾ�����г������������е�һ�֡� ���磬��������泯�ϣ�����������ʾ���˵�����

    from microbit import *

    while True:
        gesture = accelerometer.current_gesture()
        if gesture == "face up":
            display.show(Image.HAPPY)
        else:
            display.show(Image.ANGRY)

Once again, because we want the device to react to changing circumstances we
use a ``while`` loop. Within the *scope* of the loop the current gesture is
read and put into ``gesture``. The ``if`` conditional checks if ``gesture`` is
equal to ``"face up"`` (Python uses ``==`` to test for equality, a single
equals sign ``=`` is used for assignment - just like how we assign the gesture
reading to the ``gesture`` object). If the gesture is equal to ``"face up"``
then use the display to show a happy face. Otherwise, the device is made to
look angry!

���ߣ���Ϊ����ϣ���豸�Բ��ϱ仯�Ļ���������Ӧ����������ʹ��whileѭ������ѭ�����ڣ���ȡ��ǰ���Ʋ��������gesture�С�if��������������Ƿ���ڡ����泯�ϡ���pythonʹ��==��Ϊ����������ʹ�õ���=������Ϊ��ֵ�����������������ν����ƶ�����ֵ��gesture����һ������������Ƶ��ڡ�face up��������ʾ����ʾһ�ſ��ֵ�����������ʾһ������������

Magic-8
+++++++

A Magic-8 ball is a toy first invented in the 1950s. The idea is to ask
it a yes/no question, shake it and wait for it to reveal the truth. It's rather
easy to turn into a program::

Magic-8����һ����20����50����״η�������ߣ���Ŀ��������һ����/������⣬ҡ�������ȴ�����ʾ���ࡣ������ߺ�������һ��������ʵ�֣�

    from microbit import *
    import random

    answers = [
        "It is certain",
        "It is decidedly so",
        "Without a doubt",
        "Yes, definitely",
        "You may rely on it",
        "As I see it, yes",
        "Most likely",
        "Outlook good",
        "Yes",
        "Signs point to yes",
        "Reply hazy try again",
        "Ask again later",
        "Better not tell you now",
        "Cannot predict now",
        "Concentrate and ask again",
        "Don't count on it",
        "My reply is no",
        "My sources say no",
        "Outlook not so good",
        "Very doubtful",
    ]

    while True:
        display.show("8")
        if accelerometer.was_gesture("shake"):
            display.clear()
            sleep(1000)
            display.scroll(random.choice(answers))

Most of the program is a list called ``answers``. The actual game is in the
``while`` loop at the end.

����Ĵ󲿷���һ����Ϊ��answer�����б�ʵ�ʵ���Ϸ�ڽ�β��whileѭ���С�

The default state of the game is to show the character ``"8"``. However, the
program needs to detect if it has been shaken. The ``was_gesture`` method uses
its argument (in this case, the string ``"shake"`` because we want to detect
a shake) to return a ``True`` / ``False`` response. If the device was shaken
the ``if`` conditional drops into its block of code where it clears the screen,
waits for a second (so the device appears to be thinking about your question)
and displays a randomly chosen answer.

��ϷĬ������ʾ�ַ���8���� ���ǣ��ó�����Ҫ������Ƿ��ѱ�ҡ���� was_gesture�������ݲ������ڱ��������ַ�����shake������Ϊ������Ҫ���ҡ�����Է�����ӦTrue / False�� ����豸��ҡ��������if������䣬����ִ�������Ļ�Ĵ��룬Ȼ��ȴ�һ���ӣ�����Ϊ�豸�ƺ�����˼���������⣩����ʾ���ѡ��Ĵ𰸡�

Why not ask it if this is the greatest program ever written? What could you do
to "cheat" and make the answer always positive or negative? (Hint: use the
buttons.)

Ϊʲô�������Ƿ�������д����ΰ��ĳ��� ������Щʲô������ƭ����ʹ�������������ģ� ����ʾ��ʹ�ð�ť����
