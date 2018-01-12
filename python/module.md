# 程序运行时默认搜索路径

通过以下代码获取

import sys

print\(sys.path\)

# 自定义模块

每一个 .py 源文件为一个模块，如果有多个模块，而且为了防止命名冲突，可以用包来管理，即新建目录将所有模块包含进来。

自定义模块的导入

1 如果模块与调用程序在同一目录，假设模块为 test.py，直接

import test

2 不同目录。设置包管理，但是在包目录下必须要有以此 “\_\_init\_\_.py” 命名的文件，可为空。将包目录添加至 sys.path 搜索路径。两种方式

1）代码添加。假设包名为 pk ，windows系统，在 C:\python 目录下

pkPath = “C:\\python\\pk”

sys.path.append\(pkPath\)

print\(sys.path\)

import test

此方法只是对当前文件有效

2\) 设置 PYTHONPATH 环境变量

PYTHONPATH  = “C:\\python”

print\(sys.path\)

import pk.test

推荐使用第二种方式，可对所有文件有效，而且在编辑器中代码的提示功能能用。

