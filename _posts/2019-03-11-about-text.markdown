---
layout: post
title:  "关于Python中的文本"
date:   2019-03-11 15:45:00 +0800
categories: [note, python]
---

# note

Python 2:
- str: 字节序列
- unicode: 可读字符串

str.decode('utf-8') -> unicode
unicode.encode('utf-8') -> str

Python 3:
- str: 可读字符串，约等于Python 2的unicode
- bytes/bytearray: 字节序列，不等于Python 2中的bytes和str

str.encode('utf-8') -> bytes
bytes.decode('utf-8') -> str
