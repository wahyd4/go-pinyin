go-pinyin
=========

[![Join the chat at https://gitter.im/mozillazg/go-pinyin](https://badges.gitter.im/mozillazg/go-pinyin.svg)](https://gitter.im/mozillazg/go-pinyin?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![Build Status](https://travis-ci.org/mozillazg/go-pinyin.svg?branch=master)](https://travis-ci.org/mozillazg/go-pinyin)
[![Coverage Status](https://coveralls.io/repos/mozillazg/go-pinyin/badge.png?branch=master)](https://coveralls.io/r/mozillazg/go-pinyin?branch=master)
[![GoDoc](https://godoc.org/github.com/mozillazg/go-pinyin?status.svg)](https://godoc.org/github.com/mozillazg/go-pinyin)

汉语拼音转换工具 Go 版。


Installation
------------

```
go get -u github.com/mozillazg/go-pinyin
```

install CLI tool:

```
go get -u github.com/mozillazg/go-pinyin/pinyin
$ pinyin 中国人
zhōng guó rén
```


Documentation
--------------

API documentation can be found here:
https://godoc.org/github.com/mozillazg/go-pinyin


Usage
------

```go
package main

import (
	"fmt"
	"github.com/mozillazg/go-pinyin"
)

func main() {
	hans := "中国人"
	// 默认
	a := pinyin.NewArgs()
	fmt.Println(pinyin.Pinyin(hans, a))
	// [[zhong] [guo] [ren]]

	// 包含声调
	a.Style = pinyin.Tone
	fmt.Println(pinyin.Pinyin(hans, a))
	// [[zhōng] [guó] [rén]]

	// 声调用数字表示
	a.Style = pinyin.Tone2
	fmt.Println(pinyin.Pinyin(hans, a))
	// [[zho1ng] [guo2] [re2n]]

	// 开启多音字模式
	a = pinyin.NewArgs()
	a.Heteronym = true
	fmt.Println(pinyin.Pinyin(hans, a))
	// [[zhong zhong] [guo] [ren]]
	a.Style = pinyin.Tone2
	fmt.Println(pinyin.Pinyin(hans, a))
	// [[zho1ng zho4ng] [guo2] [re2n]]
}
```


Related Projects
-----------------

* [hotoo/pinyin](https://github.com/hotoo/pinyin): 汉语拼音转换工具 Node.js/JavaScript 版。
* [mozillazg/python-pinyin](https://github.com/mozillazg/python-pinyin): 汉语拼音转换工具 Python 版。
* [mozillazg/rust-pinyin](https://github.com/mozillazg/rust-pinyin): 汉语拼音转换工具 Rust 版。
