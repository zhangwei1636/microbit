Introduction
------------
����

We suggest you download and use the `mu editor <http://codewith.mu/>`_ when
working through these tutorials. Instructions for downloading and installing
Mu are on its website. You may need to install a driver, depending on your
platform (instruction are on the website).

���ǽ�����ʹ����Щ�̳�ʱ���ز�ʹ��mu�༭���� �й����غͰ�װMu��˵�������������վ��
��������Ҫ��װ�������򣬾���ȡ��������ƽ̨��˵������վ�ϣ���

Mu works with Windows, OSX and Linux.

Mu������Windows��OSX��Linux��

Once Mu is installed connect your micro:bit to your computer via a USB lead.

��װMu��ͨ��USB�߽�micro��bit���ӵ��������

Write your script in the editor window and click the "Flash" button to transfer
it to the micro:bit. If it doesn't work, make sure your micro:bit appears as
a USB storage device in your file system explorer.

�ڱ༭�������б�д�ű���Ȼ�󵥻���Flash����ť���䴫�䵽micro:bit�� ������������ã�
��ȷ������micro:bit����Դ����������ʾΪUSB�洢�豸��

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

Python�������������еı������֮һ�� ÿ�죬����ܶ�������ʶ��ʹ��Python��д�������
 ���ֹ�˾����֯����Python���ڸ��ָ�����Ӧ�ó��� �ȸ衢�������Һ��պ���֡��������С�
��ʿ�ᡢŷ�޺����о����ģ�YouTube��Mozilla������ - �������������Ǿ��á���ѧ����������������

For example, do you remember the announcement of the `discovery of gravitational waves <http://www.bbc.co.uk/news/science-environment-35552207>`_? The instruments used to make the measurements were controlled `with Python <https://www.reddit.com/r/IAmA/comments/45g8qu/we_are_the_ligo_scientific_collaboration_and_we/czxnlux>`_.

���磬�㻹�ǵ÷�������������Ϣ�� ���ڽ��в�������������Python���Ƶġ�

Put simply, if you teach or learn Python, you are developing a highly valuable
skill that applies to all areas of human endeavour.

�����֮����������ڻ�ѧϰPython�������ڿ���һ������������Ŭ������������ĸ߶��м�ֵ�ļ��ܡ�

One such area is the BBC's amazing micro:bit device. It runs a version of
Python called MicroPython that's designed to run on small computers like the BBC
micro:bit. It's a full implementation of Python 3 so when you move onto other
things (such as programming Python on a Raspberry Pi) you'll use exactly the
same language.

����һ��������BBC���˾�̾��micro��bit�豸�� ������һ����ΪMicroPython��Python�汾��
�������Ϊ����BBC micro��bit��С�ͼ���������С� ����Python 3������ʵ�֣���˵���ת��
���������������Raspberry Pi�ϱ��Python��ʱ������ʹ����ȫ��ͬ�����ԡ�

MicroPython does not include all the standard code libraries that come with
"regular" Python. However, we have created a special ``microbit`` module in
MicroPython that lets you control the device.

MicroPython�����������桱Python���������б�׼����⡣ ���ǣ�������MicroPython��
������һ�������microbitģ�飬�������������豸��

Python and MicroPython are free software. Not only does this mean you don't pay
anything to use Python, but you are also free to contribute back to the Python
community. This may be in the form of code, documentation, bug reports, running
a community group or writing tutorials (like this one). In fact, all the Python
related resources for the BBC micro:bit have been created by an international
team of volunteers working in their free time.

Python��MicroPython���������� �ⲻ����ζ��������Ҫ֧���κη�����ʹ��Python������
��ҲҪ���ɵػ���Python������ ������Ǵ��롢�ĵ������󱨸桢������������߱�д�̳�
���籾�̳̣�����ʽ�� ��ʵ�ϣ�BBC micro��bit������Python�����Դ������һ������־Ը��
�Ŷ��ڿ���ʱ�䴴���ġ�

These lessons introduce MicroPython and the BBC
micro:bit in easy-to-follow steps. Feel free to adopt and adapt them for
classroom based lessons, or perhaps just follow them on your own at home.

��Щ�γ��Լ򵥵�һ�����Ĳ������MicroPython��BBC micro��bit�� ������������ú͵���������
�ڿ��ý�ѧ��Ҳ�����ڼ����Լ�һ�����ظ��Ž̳�ѧϰ��

You'll have most success if you explore, experiment and play. You can't break
a BBC micro:bit by writing incorrect code. Just dive in!

��������̽����ʵ�����Ϸ���㽫������ĳɹ��� �㲻��ͨ����д����Ĵ������ƻ�BBC micro��bit�����ܲ����ɣ�

A word of warning: *you will fail many times*, and that is fine. **Failure is
how good software developers learn**. Those of us who work as software
developers have a lot of fun tracking down bugs and avoiding the repetition of
mistakes.

һ�侯�棺�����ʧ�ܣ��ǲ����¡�ʧ�������������Աѧϰ�ĺ÷�������Ϊ���������Ա�����ٴ���ͱ����ظ����������������С�

If in doubt, remember the Zen of MicroPython::

��������ʣ����סMicroPython�ĸ��ԣ�

    Code,
    Hack it,
    Less is more,
    Keep it simple,
    Small is beautiful,

    Be brave! Break things! Learn and have fun!
    Express yourself with MicroPython.

    Happy hacking! :-)

Best of luck!

         ���룬
???? ������
???? �ټ��Ƕ࣬
???? ������򵥻���
???? С������

???? �¸������� ����һ�У� ����ѧ��
???? ��MicroPython����Լ���

???? ���ֵĺڿͣ�

ף����ˣ�
