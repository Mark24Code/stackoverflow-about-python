| rank | ▲ | ✰ | vote | url |
|:-:|:-:|:-:|:-:|:-:|
|  30  |  554 | 230 | 447 | [url](http://stackoverflow.com/questions/287871/print-in-terminal-with-colors-using-python) |

***

## 怎么在终端里输出颜色?

怎么样用Python在终端里输出带颜色的文本?最好的代替块字符的unicode字符是什么?(What is the best Unicode symbol to represent a solid block?这句话没理解)

***

这依赖于你用哪种操作系统.最常用的方法就是输出ANSI转义序列.例如,下面的:

```python
class bcolors:
    HEADER = '\033[95m'
    OKBLUE = '\033[94m'
    OKGREEN = '\033[92m'
    WARNING = '\033[93m'
    FAIL = '\033[91m'
    ENDC = '\033[0m'
```

可以这么用上面的代码:

```python
print bcolors.WARNING + "Warning: No active frommets remain. Continue?" + bcolors.ENDC
```

这种方法适合OS X,linux和windows系统.还有一些其他的ansi代码可以设置颜色,消除光标或者其他.

如果想要应用更复杂的功能(听起来像是如果你正在写一个游戏),你应该看看"curses"模块,它包含了许多关于次部分复杂操作.[Python Curses HowTO](https://docs.python.org/2/howto/curses.html)可以作为好的介绍.

如果你不使用拓展的ASCII(比如不是一个PC),`#`或者`@`可能是你最好的选择.如果你用的是[IBM扩展ascii字符设置](http://telecom.tbi.net/asc-ibm.html),你还可以有更多的选择.176,177,178和219是"块字符"

一些现代的基于文本的程序,像"Swarf Fortress",显示的文本使用图像模式,而用的字体也是传统的计算机字体的图像.你可以在[Dwarf Fortress Wiki](http://dwarffortresswiki.org/DF2014:Tilesets)找到你可以用的字符.

[Text Mode Demo Contest ](http://en.wikipedia.org/wiki/Text_Mode_Demo_Contest)也有许多资料可供参考.

我想可能有点跑题了.我在设计一个史诗级别的基于文本的冒险游戏.祝你好运!

***

怎么就没人提[Python termcolor module](https://pypi.python.org/pypi/termcolor).用法相当简单:

```python
from termcolor import colored

print colored('hello', 'red'), colored('world', 'green')
```

虽然有点简单,但是对于游戏程序和你想要的"colored blocks"来说足够了.
