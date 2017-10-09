---
title: A little thought about learning Python
date: 2017-10-09 10:58:45
tags: 生活体察记录, Python
---

自学 Python 已经一年有余，中间有些断续，一直以来如果是跟着 Coursera 上面走或者跟着教 Python 的 English Books 走的话，会跟着上面的练习题编写小程序。如果没有练习题的话就不回去动手找些东西来弄。不是没有想过自己找个生活中的东西来弄，而是一想到现在学的还都是皮毛，变不了这些东西，所以想法一直在脑袋里面盘旋，没有落实。其实，原因有很多，比如编写程序时各种的拼写错误，打字的节奏，容易出现语法的错误等等，这些也是不愿意动手的原因，本质上，是因为对于命令行之类的东西还是不甚熟悉，所以有些畏惧不愿尝试。而前些日子较为系统地学习了 Linux 的常用命令和示例，现在对命令行这种东西又了更大的兴趣，也开始对之熟悉起来，如今在 Mac 上面进行很多操作，比如查找文件，打开文件时，开始用 terminal 操作，感觉确实很不错，尤其是在批量查找、删除某类型的文件时，用 command line 显得尤为方便和快速，command line 能够实现的高级搜索、删除、新建、重命名等操作如果用 Graphic Interface 的话要不就是很难实现或者极为不方便，操作的手法即笨拙又漫长。

所以，今后操作 Mac 与 Linux 的相关操作要尽可能的用 command line 来实现，这也是一个合格的程序员需要具备的最基本的要求，这也说明了为什么大多数企业招聘 programmer 往往要求具有一定的 Linux 基础的原因。如果对 command line 不熟悉，那么将会极大的影响编程效率。事实上 command line 也可以算作是编程语言的一个分支，就像 regular expression 一样，都极为通用，一旦对 command line 的各种操作变的特别熟悉之后，那么对于进阶其他的快捷键、各种 programmer 常用的软件，比如 Atom、Sublime、Typora、Markdown句法等等就如同信手拈来，像 Mac 的 terminal 与 Windows 的 cmd 等更不在话下。所以，对于 command line 需要彻底掌握，command line、regular expression、anyone programing language、database，只要精通前三者、最后一个，那么一个 programmer 应该算得上是一个高手了吧？

所以，接下来，对于 command line 和 regular expression 需要放在一起学，另外 regular expression 除了需要与 command line 放在一起学，还需要与 programming language 放在一起来学，尤其是对于文字、符号的处理会变的几位高效。而 database 则需要与 language 放在一起来练习。用 language 处理后的数据需要进行系统的存储，这样可以方便后续的查找和使用，如果仅仅把它们零碎的放在各个文件里面，会显得极为不方面。就像昨天编写的那个用户平台登陆程序一样，如果能够把相关的数据存入 database ，会是一个极好的选择，当然，这个程序如果存储数据不多，也可以把它们简单的放在文件里面。限免贴上昨天编写的很简单的一个小程序：

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Sun Oct  8 16:26:47 2017

@author: larrybrin
"""

name_dict = []
passwd_dict = []

def newusers():
    global name_dict, passwd_dict
    name = input('Please input the name you choose: ')
    while name in name_dict:
        input('The name has been taken by others, input another one: ')
    passwd = input('Set your passsword: ')
    name_dict.append(name)
    passwd_dict.append(passwd)

def oldusers():
    global name_dict, passwd_dict
    name = input('Please input your username:')
    passwd = input('Please input your passsword: ')
    while name not in name_dict or passwd not in passwd_dict:
        print('login incorrect: ')
        name = input('Please input your username:')
        passwd = input('Please input your passsword: ')
    print(name, 'welcome back ')

def login():
    inputs = True
    options = """
            (N)ew User Login
            (O)ld User Login
            (E)xit
            """
    print(options)
    while inputs:
        option = input('Choose one character in the parenthesis: ')
        try:
            if option == 'N':
                inputs = False
                newusers()
            elif option == 'O':
                inputs = False
                oldusers()
            elif option == 'E':
                inputs = False
                break
        except:
            print('Your input is illegal, try again!')   

if __name__ == '__main__':
    login()
```

这个程序存在很多漏洞，最大的漏洞有两个：一个是用户信息不能存储，另一个是用户如果选择 olduser 登陆，如果他的信息本身未曾录入到系统数据的话， 那么他在输入时就会变的无限循环，一直提醒重新输入用户名和密码，而不能跳入到新用户的注册进程中。换句话说，这个小程序还有很大的完善空间。

另外，红远需要注意的是，你的 python 语言基本框架已经搭建完毕，接下来的主要工作是放在用上，需要自己动手想一些需要用编程解决的问题，然后用 python 来解决，如果遇到某个难点，可以进行搜索查找，今后深化 Python  的不能再是拿着一本书从头啃到位，这样做速度既慢而且收效不大。因为现在 Python 的学习基本框架已经搭建完毕，剩下的则是对其进行修修补补。目前最需要解决的问题是，使用 python 解决能够解决的各种问题，一次来达到对 python 语言的进一步熟悉，直至掌握。而现在你对其中的一些基本的 function 和 method 还不甚掌握，唯一能够解决这个问题的途径就是不断地练习，哪里弱，就练习哪里。除此之外，你应该开始着手搭建 database 的框架，理解 Python 第三方库的基本用途，这些是完善 Python 框架的必要工作。

而现在，除去与编程直接相关的事务，就是与工作相关的事物，要开始写简历啦！尽管不知从何着手，但这件事情不能再拖下去，要把握好时机。

哦，对了，git 相关的基本操作也需要掌握好。