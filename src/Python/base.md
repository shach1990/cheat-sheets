## Python基础
- 文档注释（Docstring）
	- 作为文档的Docstring一般出现在模块头部、函数和类的头部，这样在python中可以通过对象的__doc__对象获取文档. 编辑器和IDE也可以根据Docstring给出自动提示.
	- 文档注释以 `"""` 开头和结尾, 首行不换行, 如有多行, 末行必需换行
- 三引号 `''' '''`
- 算数运算符
	- `**` 幂--返回x的y次方，示例：2**3，2的3次方
	- `//` 取整数--返回商的整数部分
	
    		>>> 11//2
            5
            >>> 11//2.0
            5.0
            >>> 11.0//2.0
            5.0
            >>> 11.00//2.0
            5.0
            >>> 11.00//2.00
            5.0
            >>> 11.0//2
            5.0

- 空值，在 Python 中，用 None 来表示
- 当Python 解释器读取源代码时，为了让它按 UTF-8 编码读取，我们通常在文件开头写上这两行：

		#!/usr/bin/env python3
		# -*- coding: utf-8 -*-