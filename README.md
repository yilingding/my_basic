	 __   __  __   __         _______  _______  _______  ___   _______ 
	|  |_|  ||  | |  |       |  _    ||   _   ||       ||   | |       |
	|       ||  |_|  | ____  | |_|   ||  |_|  ||  _____||   | |       |
	|       ||       ||____| |       ||       || |_____ |   | |       |
	|       ||_     _|       |  _   | |       ||_____  ||   | |      _|
	| ||_|| |  |   |         | |_|   ||   _   | _____| ||   | |     |_ 
	|_|   |_|  |___|         |_______||__| |__||_______||___| |_______|

**Copyright (C) 2011 - 2017 [Wang Renxin](https://linkedin.com/in/wangrenxin). All rights reserved.**

[![Build status](https://travis-ci.org/paladin-t/my_basic.svg?branch=master)](https://travis-ci.org/paladin-t/my_basic)
[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)

[简体中文](https://github.com/paladin-t/my_basic/wiki/%E7%94%B1%E7%BA%AF-C-%E8%AF%AD%E8%A8%80%E7%BC%96%E5%86%99%E7%9A%84-BASIC-%E8%84%9A%E6%9C%AC%E8%A7%A3%E9%87%8A%E5%99%A8)

[开发日志](http://blog.sina.com.cn/s/articlelist_1584387113_12_1.html)

## Contents

* [Introduction](#introduction)
* [Compatibility](#compatibility)
* [Main features](#main-features)
* [Script at a glance](#script-at-a-glance)
* [Related projects](#related-projects)
* [Installation](#installation)
* [Interpreter workflow diagram](#interpreter-workflow-diagram)
* [Wiki](#wiki)
* [References](#references)
* [Support MY-BASIC development/List of donors](#support-my-basic-developmentlist-of-donors)

## Introduction

MY-BASIC is a lightweight cross-platform easy extendable BASIC interpreter written in pure C with about twenty thousand lines of source code. MY-BASIC is a dynamic typed programming language. It supports structured grammar, and implements a style of OOP called [prototype-based programming](https://en.wikipedia.org/wiki/Prototype-based_programming) paradigm, furthermore it offers a functional programming ability with [lambda abstraction](https://en.wikipedia.org/wiki/Anonymous_function). It is aimed to be either an embeddable scripting language or a standalone interpreter. The core is very lightweight; all in a C source file and an associated header file; simpleness of source file layout and tightness dependency make it extraordinarily tough. Anyone even C programming newbies could learn how to use it and add new scripting interfaces in five minutes. It's able to easily combine MY-BASIC with an existing project in C, C++, Java, Objective-C, Swift, C# and many other languages. Script driven can make your projects more powerful, elegant and neat. It's also possible to learn how to build an interpreter from scratch with MY-BASIC, or build your own dialect easily based on it.

"MY-" in the name could be understood literally as "My" or "Make Your", it's up to you.

## Compatibility

It fits well on a large scale of Workstation, PC, Tablet, Pad, Mobile Phone, PDA, Video Game Console, Raspberry Pi, Intel Edison, Arduino and even MCU; totally portable to Windows, macOS, Unix, Linux, iOS, Android, RTOS, etc.

**For Arduino**

There is a MY-BASIC interpreter porting of Arduino, with a totally rewritten shell and user manual. Please see [MY-BASIC ARDU](https://my-basic.github.io/my_basic_ardu/).

<a href="https://my-basic.github.io/my_basic_ardu/">
<img src="https://upload.wikimedia.org/wikipedia/commons/8/87/Arduino_Logo.svg" width="64">
</a>

## Main features

MY-BASIC is a dynamic typed programming language with BASIC syntax and has a very dynamic nature; it makes it flexible and easy to use. MY-BASIC offers a wide range of features including:

* It is totally **free** to use MY-BASIC for commercial or noncommercial purpose under the MIT license
* Written in clean **ANSI C**, source code is portable to a dozen of platforms
* **Lightweight** (within memory usage less than 128KB), fast, and cuttable
* With both retro and modern BASIC syntax
* Case-insensitive tokenization, and many other indelible BASIC feelings
* [Unicode support](https://github.com/paladin-t/my_basic/wiki/Support-for-Unicode)
* **[Prototype-based programming](https://en.wikipedia.org/wiki/Prototype-based_programming)** (OOP) paradigm, with reflection support
* **[Lambda abstraction](https://en.wikipedia.org/wiki/Anonymous_function)** enhanced functional programming
* **Dynamic typed** integer, real, string, boolean, usertype, etc. with array support
* Standard numeric functions, and standard string functions
* Referenced usertype support
* Collection implementation and manipulation functions for **`LIST`** and **`DICT`**
* Automatic releasing of referenced objects (list, dictionary, referenced usertype, prototype, lambda, etc.) benefited from **Reference Counting** and **Garbage Collection**
* Multiple source file support by `IMPORT` statement
* Structured user customizable **sub routine** definition by **`DEF/ENDDEF`** support, including tail recursion optimization
* Structured `IF/THEN/ELSEIF/ELSE/ENDIF` support
* Structured `FOR/TO/STEP/NEXT`, `FOR/IN/NEXT`, `WHILE/WEND`, `DO/UNTIL` support
* Reserved retro `GOTO`, `GOSUB/RETURN` support
* Debug APIs
* Customizable memory pool
* High expansibility, easy to use APIs, easy to write customized scripting interfaces
* Powerful interactive ability to manipulate script facilities at native side; or to use native functionalities in script, and vice versa
* More features under development

You may wondering if it's possible to introduce another feature to MY-BASIC, you may would like to take a look at [this page](https://github.com/paladin-t/my_basic/wiki/Is-it-possible-to-introduce-another-feature). You may also would like to take a look at the [language design](https://github.com/paladin-t/my_basic/wiki/Language-design) to find some of my plan.

## Script at a glance

Come along with a traditional "Hello World" script in MY-BASIC:

~~~~~~~~~~bas
input "What is your name: ", n$

def foo(a, b)
	return a + " " + b + " by " + n$ + "."
enddef

print foo("Hello", "world");
~~~~~~~~~~

Read the [MY-BASIC Quick Reference](https://paladin-t.github.io/my_basic/MY-BASIC%20Quick%20Reference.pdf) (especially the "**Programming with BASIC**" section) to get more details about how to program in MY-BASIC.

## Related projects

I've been making some other projects, which make use of MY-BASIC, and make more benefits.

* [MY-BASIC Code Editor (Unity)](https://github.com/my-basic/my_basic_code_editor_unity)
	- A code editor for MY-BASIC powered by the Unity3D engine.

## Installation

### Use standalone interpreter binary

This repository contains precompiled binaries for [Windows](output/my_basic.exe) and [macOS](output/my_basic_mac), it's easy to download one of them and have a first impressive playground. Or you could make a build as follow:

* Open the Visual Studio solution `my_basic.sln` on Windows to build an executable
* Open the Xcode solution `my_basic_mac.xcodeproj` on macOS to build a macOS executable
* If you were using other *nix OS, then use the `makefile` with a "make" toolchain to build an interpreter binary according to your specific platform

To compile an interpreter binary for your own platform manually, please follow the steps:

1. Retrieve at least [`core`](core) and [`shell`](shell) folders for a minimum build
2. Setup your compile toolchain configuration
3. Compile [`core/my_basic.c`](core/my_basic.c) and [`shell/main.c`](shell/main.c), they both require [`core/my_basic.h`](core/my_basic.h); then link up your own executable

The standalone interpreter supports three running modes:

* Execute the binary without arguments to enter the interactive mode of MY-BASIC
* Pass a file path to the binary to load and run that script file directly
* Pass an argument `-e` followed by an expression to evaluate it and print the result, eg. `-e "2 * (3 + 4)"`

Type "HELP" and hint Enter under interactive mode to view full detail usage of the interpreter.

### Combine with exist projects

MY-BASIC is cleanly written in a single C source file and an associated header file. Just copy [`core/my_basic.c`](core/my_basic.c) and [`core/my_basic.h`](core/my_basic.h) to your project folder and add them to a build configuration.

You can definitely [link with MY-BASIC as a lib](https://github.com/paladin-t/my_basic/wiki/Link-with-MY_BASIC) as well.

For more details about using MY-BASIC when it has be integrated with a project, please see [MY-BASIC Quick Reference](https://paladin-t.github.io/my_basic/MY-BASIC%20Quick%20Reference.pdf) or read the [Wiki](#wiki) pages.

## [Interpreter workflow diagram](https://github.com/paladin-t/my_basic/wiki/Interpreter-workflow-diagram)

It's necessary to know some principle of MY-BASIC before doing deep customization; nothing's better than a workflow diagram to get a first image.

![](https://github.com/paladin-t/my_basic/wiki/img/workflow.png)

More detail are issued on the [Wiki](#wiki) pages.

## [Wiki](https://github.com/paladin-t/my_basic/wiki)

The [MY-BASIC Quick Reference](https://paladin-t.github.io/my_basic/MY-BASIC%20Quick%20Reference.pdf) includes most of the fundamental topics, however, it hasn't covered everything, such as the design principle, machinism behind MY-BASIC, effective practice, etc; all of them are issued in the [Wiki](https://github.com/paladin-t/my_basic/wiki):

* Principles
	* [Language design](https://github.com/paladin-t/my_basic/wiki/Language-design)
	* [How lambda works](https://github.com/paladin-t/my_basic/wiki/How-lambda-works)
	* [Passes](https://github.com/paladin-t/my_basic/wiki/Passes)
	* [Interpreter workflow diagram](https://github.com/paladin-t/my_basic/wiki/Interpreter-workflow-diagram)
* Code with MY-BASIC
	* [Support for Unicode](https://github.com/paladin-t/my_basic/wiki/Support-for-Unicode)
	* [Import another file](https://github.com/paladin-t/my_basic/wiki/Import-another-file)
	* [Module (namespace)](https://github.com/paladin-t/my_basic/wiki/Module-(namespace))
	* [Sub routine](https://github.com/paladin-t/my_basic/wiki/Sub-routine)
	* [Lambda abstraction](https://github.com/paladin-t/my_basic/wiki/Lambda-abstraction)
	* [Structured exception handling](https://github.com/paladin-t/my_basic/wiki/Structured-exception-handling)
	* [Multiple condition](https://github.com/paladin-t/my_basic/wiki/Multiple-condition)
* Understanding data type system in MY-BASIC
	* [Collection manipulation](https://github.com/paladin-t/my_basic/wiki/Collection-manipulation)
	* [Manipulate an array](https://github.com/paladin-t/my_basic/wiki/Manipulate-an-array)
	* [Automatic memory management](https://github.com/paladin-t/my_basic/wiki/Automatic-memory-management)
	* [Use usertype values](https://github.com/paladin-t/my_basic/wiki/Use-usertype-values)
	* [Use prototype-based class](https://github.com/paladin-t/my_basic/wiki/Use-prototype-based-class)
	* [Define a class in C](https://github.com/paladin-t/my_basic/wiki/Define-a-class-in-C)
	* [Meta methods](https://github.com/paladin-t/my_basic/wiki/Meta-methods)
	* [Override operators](https://github.com/paladin-t/my_basic/wiki/Override-operators)
	* [Override functions](https://github.com/paladin-t/my_basic/wiki/Override-functions)
* Standalone shell
	* [Extra functions](https://github.com/paladin-t/my_basic/wiki/Extra-functions)
* Integration
	* [Link with MY-BASIC](https://github.com/paladin-t/my_basic/wiki/Link-with-MY_BASIC)
	* [Write a debugger](https://github.com/paladin-t/my_basic/wiki/Write-a-debugger)
	* [Callback](https://github.com/paladin-t/my_basic/wiki/Callback)
	* [Interop with C#](https://github.com/paladin-t/my_basic/wiki/Interop-with-C%23)
* Customization
	* [Customize macros](https://github.com/paladin-t/my_basic/wiki/Customize-macros)
	* [Customize a memory allocator](https://github.com/paladin-t/my_basic/wiki/Customize-a-memory-allocator)
	* [Redirect PRINT and INPUT](https://github.com/paladin-t/my_basic/wiki/Redirect-PRINT-and-INPUT)
	* [Redefine int_t and real_t](https://github.com/paladin-t/my_basic/wiki/Redefine-int_t-and-real_t)
	* [Convert between string and real](https://github.com/paladin-t/my_basic/wiki/Convert-between-string-and-real)
	* [Customize an importer](https://github.com/paladin-t/my_basic/wiki/Customize-an-importer)
* [More scripting APIs](https://github.com/paladin-t/my_basic/wiki/More-scripting-APIs)
	* [String matching module](https://github.com/paladin-t/my_basic/wiki/String-matching-module)
	* [String manipulation module](https://github.com/paladin-t/my_basic/wiki/String-manipulation-module)
	* [File module](https://github.com/paladin-t/my_basic/wiki/File-module)
	* [Inline data sequence module](https://github.com/paladin-t/my_basic/wiki/Inline-data-sequence-module)
	* [Bit operation module](https://github.com/paladin-t/my_basic/wiki/Bit-operation-module)
	* [Miscellaneous module](https://github.com/paladin-t/my_basic/wiki/Miscellaneous-module)
	* [Stack module](https://github.com/paladin-t/my_basic/wiki/Stack-module)
* [FAQ](https://github.com/paladin-t/my_basic/wiki/FAQ)
	* [Is it possible to introduce another feature](https://github.com/paladin-t/my_basic/wiki/Is-it-possible-to-introduce-another-feature)

## References

* [BASIC - Wikipedia](http://en.wikipedia.org/wiki/BASIC)
* [Prototype-based programming - Wikipedia](https://en.wikipedia.org/wiki/Prototype-based_programming)
* [Lambda abstraction - Wikipedia](https://en.wikipedia.org/wiki/Anonymous_function)

## Support MY-BASIC development/List of donors

You can support MY-BASIC development with a [donation](http://paladin-t.github.io/my_basic/donate.html).

<a href="http://paladin-t.github.io/my_basic/donate.html">
<img src="https://github.com/paladin-t/my_basic/wiki/img/button_donate.png" width="128">
</a>

Or see the [list of donors](http://paladin-t.github.io/my_basic/donate.html).
