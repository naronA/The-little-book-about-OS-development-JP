# Contents
* [1 Introduction](#introduction)
  * [1.1 About the Book](#about-the-book)
  * [1.2 The Reader](#the-reader)
  * [1.3 Credits, Thanks and Acknowledgements](#credits-thanks-and-acknowledgements)
  * [1.4 Contributors](#contributors)
  * [1.5 Changes and Corrections](#changes-and-corrections)
  * [1.6 Issues and where to get help](#issues-and-where-to-get-help)
  * [1.7 License](#license)
* [2 First Steps](#first-steps)
  * [2.1 Tools](#tools)
    * [2.1.1 Quick Setup](#quick-setup)
    * [2.1.2 Programming Languages](#programming-languages)
    * [2.1.3 Host Operating System](#host-operating-system)
    * [2.1.4 Build System](#build-system)
    * [2.1.5 Virtual Machine](#virtual-machine)
  * [2.2 Booting](#booting)
    * [2.2.1 BIOS](#bios)
    * [2.2.2 The Bootloader](#the-bootloader)
    * [2.2.3 The Operating System](#the-operating-system)
  * [2.3 Hello Cafebabe](#hello-cafebabe)
    * [2.3.1 Compiling the Operating System](#compiling-the-operating-system)
    * [2.3.2 Linking the Kernel](#linking-the-kernel)
    * [2.3.3 Obtaining GRUB](#obtaining-grub)
    * [2.3.4 Building an ISO Image](#building-an-iso-image)
    * [2.3.5 Running Bochs](#running-bochs)
  * [2.4 Further Reading](#further-reading)
* [3 Getting to C](#getting-to-c)
  * [3.1 Setting Up a Stack](#setting-up-a-stack)
  * [3.2 Calling C Code From Assembly](#calling-c-code-from-assembly)
    * [3.2.1 Packing Structs](#packing-structs)
  * [3.3 Compiling C Code](#compiling-c-code)
  * [3.4 Build Tools](#build-tools)
  * [3.5 Further Reading](#further-reading-1)
* [4 Output](#output)
  * [4.1 Interacting with the Hardware](#interacting-with-the-hardware)
  * [4.2 The Framebuffer](#the-framebuffer)
    * [4.2.1 Writing Text](#writing-text)
    * [4.2.2 Moving the Cursor](#moving-the-cursor)
    * [4.2.3 The Driver](#the-driver)
  * [4.3 The Serial Ports](#the-serial-ports)
    * [4.3.1 Configuring the Serial Port](#configuring-the-serial-port)
    * [4.3.2 Configuring the Line](#configuring-the-line)
    * [4.3.3 Configuring the Buffers](#configuring-the-buffers)
    * [4.3.4 Configuring the Modem](#configuring-the-modem)
    * [4.3.5 Writing Data to the Serial Port](#writing-data-to-the-serial-port)
    * [4.3.6 Configuring Bochs](#configuring-bochs)
    * [4.3.7 The Driver](#the-driver-1)
  * [4.4 Further Reading](#further-reading-2)
* [5 Segmentation](#segmentation)
  * [5.1 Accessing Memory](#accessing-memory)
  * [5.2 The Global Descriptor Table (GDT)](#the-global-descriptor-table-gdt)
  * [5.3 Loading the GDT](#loading-the-gdt)
  * [5.4 Further Reading](#further-reading-3)
* [6 Interrupts and Input](#interrupts-and-input)
  * [6.1 Interrupts Handlers](#interrupts-handlers)
  * [6.2 Creating an Entry in the IDT](#creating-an-entry-in-the-idt)
  * [6.3 Handling an Interrupt](#handling-an-interrupt)
  * [6.4 Creating a Generic Interrupt Handler](#creating-a-generic-interrupt-handler)
  * [6.5 Loading the IDT](#loading-the-idt)
  * [6.6 Programmable Interrupt Controller (PIC)](#programmable-interrupt-controller-pic)
  * [6.7 Reading Input from the Keyboard](#reading-input-from-the-keyboard)
  * [6.8 Further Reading](#further-reading-4)
* [7 The Road to User Mode](#the-road-to-user-mode)
  * [7.1 Loading an External Program](#loading-an-external-program)
    * [7.1.1 GRUB Modules](#grub-modules)
  * [7.2 Executing a Program](#executing-a-program)
    * [7.2.1 A Very Simple Program](#a-very-simple-program)
    * [7.2.2 Compiling](#compiling)
    * [7.2.3 Finding the Program in Memory](#finding-the-program-in-memory)
    * [7.2.4 Jumping to the Code](#jumping-to-the-code)
  * [7.3 The Beginning of User Mode](#the-beginning-of-user-mode)
* [8 A Short Introduction to Virtual Memory](#a-short-introduction-to-virtual-memory)
  * [8.1 Virtual Memory Through Segmentation?](#virtual-memory-through-segmentation)
  * [8.2 Further Reading](#further-reading-5)
* [9 Paging](#paging)
  * [9.1 Why Paging?](#why-paging)
  * [9.2 Paging in x86](#paging-in-x86)
    * [9.2.1 Identity Paging](#identity-paging)
    * [9.2.2 Enabling Paging](#enabling-paging)
    * [9.2.3 A Few Details](#a-few-details)
  * [9.3 Paging and the Kernel](#paging-and-the-kernel)
    * [9.3.1 Reasons to Not Identity Map the Kernel](#reasons-to-not-identity-map-the-kernel)
    * [9.3.2 The Virtual Address for the Kernel](#the-virtual-address-for-the-kernel)
    * [9.3.3 Placing the Kernel at `0xC0000000`](#placing-the-kernel-at-0xc0000000)
    * [9.3.4 Higher-half Linker Script](#higher-half-linker-script)
    * [9.3.5 Entering the Higher Half](#entering-the-higher-half)
    * [9.3.6 Running in the Higher Half](#running-in-the-higher-half)
  * [9.4 Virtual Memory Through Paging](#virtual-memory-through-paging)
  * [9.5 Further Reading](#further-reading-6)
* [10 Page Frame Allocation](#page-frame-allocation)
  * [10.1 Managing Available Memory](#managing-available-memory)
    * [10.1.1 How Much Memory is There?](#how-much-memory-is-there)
    * [10.1.2 Managing Available Memory](#managing-available-memory-1)
  * [10.2 How Can We Access a Page Frame?](#how-can-we-access-a-page-frame)
  * [10.3 A Kernel Heap](#a-kernel-heap)
  * [10.4 Further reading](#further-reading-7)
* [11 User Mode](#user-mode)
  * [11.1 Segments for User Mode](#segments-for-user-mode)
  * [11.2 Setting Up For User Mode](#setting-up-for-user-mode)
  * [11.3 Entering User Mode](#entering-user-mode)
  * [11.4 Using C for User Mode Programs](#using-c-for-user-mode-programs)
    * [11.4.1 A C Library](#a-c-library)
  * [11.5 Further Reading](#further-reading-8)
* [12 File Systems](#file-systems)
  * [12.1 Why a File System?](#why-a-file-system)
  * [12.2 A Simple Read-Only File System](#a-simple-read-only-file-system)
  * [12.3 Inodes and Writable File Systems](#inodes-and-writable-file-systems)
  * [12.4 A Virtual File System](#a-virtual-file-system)
  * [12.5 Further Reading](#further-reading-9)
* [13 System Calls](#system-calls)
  * [13.1 Designing System Calls](#designing-system-calls)
  * [13.2 Implementing System Calls](#implementing-system-calls)
  * [13.3 Further Reading](#further-reading-10)
* [14 Multitasking](#multitasking)
  * [14.1 Creating New Processes](#creating-new-processes)
  * [14.2 Cooperative Scheduling with Yielding](#cooperative-scheduling-with-yielding)
  * [14.3 Preemptive Scheduling with Interrupts](#preemptive-scheduling-with-interrupts)
    * [14.3.1 Programmable Interval Timer](#programmable-interval-timer)
    * [14.3.2 Separate Kernel Stacks for Processes](#separate-kernel-stacks-for-processes)
    * [14.3.3 Difficulties with Preemptive Scheduling](#difficulties-with-preemptive-scheduling)
  * [14.4 Further Reading](#further-reading-11)

# <a name="introduction">1 Introduction</a>

This text is a practical guide to writing your own x86 operating system. It is designed to give enough help with the technical details while at the same time not reveal too much with samples and code excerpts. We’ve tried to collect parts of the vast (and often excellent) expanse of material and tutorials available, on the web and otherwise, and add our own insights into the problems we encountered and struggled with.

This book is not about the theory behind operating systems, or how any specific operating system (OS) works. For OS theory we recommend the book Modern Operating Systems by Andrew Tanenbaum [1]. Lists and details on current operating systems are available on the Internet.

The starting chapters are quite detailed and explicit, to quickly get you into coding. Later chapters give more of an outline of what is needed, as more and more of the implementation and design becomes up to the reader, who should now be more familiar with the world of kernel development. At the end of some chapters there are links for further reading, which might be interesting and give a deeper understanding of the topics covered.

In chapter 2 and 3 we set up our development environment and boot up our OS kernel in a virtual machine, eventually starting to write code in C. We continue in chapter 4 with writing to the screen and the serial port, and then we dive into segmentation in chapter 5 and interrupts and input in chapter 6.

After this we have a quite functional but bare-bones OS kernel. In chapter 7 we start the road to user mode applications, with virtual memory through paging (chapter 8 and 9), memory allocation (chapter 10), and finally running a user application in chapter 11.

In the last three chapters we discuss the more advanced topics of file systems (chapter 12), system calls (chapter 13), and multitasking (chapter 14).

　この文書は、x86のOSを自作するための実践的なガイドです。
この本の方針は、大量にサンプルやコードの抜粋を公開するのは避け、技術的な説明のほうを充実させています。
我々は、ウェブ等で手に入る膨大なチュートリアルや資料の一部を整理し、
それらを読んだ際に我々が悩んだ点への考察を付け加えるよう心がけました。

　この本では、OS論や特定のOSがどのように動作するのかといった内容は取り扱いません。
OS論については、Andrew Tanenbaum著のModern Operating Systems[[1]](#1)
という本をおすすめします。また昨今のOSの一覧や詳細は、インターネットから取得できます。

　すばやくコーディングに移れるようにするため、序盤の章では非常に詳細かつ厳密に説明していきます。
後半の章では、たぶんカーネル開発の世界に親しめるようになれるくらいまで、
より多くの実装やデザインの概要を紹介していきます。
いくつかの章の終わりには、そのトピックの理解をより深めるための興味をそそるリンクも書いてあります。

　2章、3章では我々とおなじ開発環境を設定したり、仮想マシンでのOSカーネルの起動したりしたのち、
最終的にはC言語でソースコードを書いていきます。4章では、スクリーンとシリアルポートについて、
5章ではセグメンテーションについて、6章ではインタラプト（割り込み）と入力について述べていきます。

　2−6章を終える頃には、機能的ではあるが必要最低限のOSカーネルが完成しているでしょう。
そして7章から、ユーザーモードでのアプリケーションについて学んでいきます、
8-9章では仮想メモリについて、10章ではメモリーアロケーションについて、
そして11章ではユーザーアプリケーションを動かします。

　最後の３つの章ではより高度なトピックについて議論します。
12章では、ファイルシステムについて、13章ではシステムコールについて、
14章ではマルチタスクについて述べます。

## <a name="about-the-book">1.1 About the Book</a>

The OS kernel and this book were produced as part of an advanced individual course at the Royal Institute of Technology [2], Stockholm. The authors had previously taken courses in OS theory, but had only minor practical experience with OS kernel development. In order to get more insight and a deeper understanding of how the theory from the previous OS courses works out in practice, the authors decided to create a new course, which focused on the development of a small OS. Another goal of the course was writing a thorough tutorial on how to develop a small OS basically from scratch, and this short book is the result.

The x86 architecture is, and has been for a long time, one of the most common hardware architectures. It was not a difficult choice to use the x86 architecture as the target of the OS, with its large community, extensive reference material and mature emulators. The documentation and information surrounding the details of the hardware we had to work with was not always easy to find or understand, despite (or perhaps due to) the age of the architecture.

The OS was developed in about six weeks of full-time work. The implementation was done in many small steps, and after each step the OS was tested manually. By developing in this incremental and iterative way, it was often easier to find any bugs that were introduced, since only a small part of the code had changed since the last known good state of the code. We encourage the reader to work in a similar way.

During the six weeks of development, almost every single line of code was written by the authors together (this way of working is also called pair-programming). It is our belief that we managed to avoid a lot of bugs due to this style of development, but this is hard to prove scientifically.

　OSカーネルとこの本はRoyal Institute of Technology(スウェーデン王立工科大学[[2]](#2))
の上級単独コースの一部として作成されました。著者は以前にOS論のコースを受講しましたが、
実践的なOSカーネル開発の経験はあまりありませんでした。以前のOSコースから学んだOSの理論が、
実装にどのように働いているのか、より深い理解を得るために、
著者は小さなOSのを開発することに焦点をおいた新しいコースをつろうと決心しました。
この新しいコースのもう一つのゴールは、小さいOSを基本的に１からつくり上げる方法の
チュートリアルを書き記すことであり、それがこの本です。

　x86アーキテクチャはかなり以前から最も一般的なハードウェアアーキテクチャです。
大きなコミュニティーもあり、おおくのリファレンスもあり、成熟したエミュレータもあるので、
OS作成にx86アーキテクチャを選ぶことは、難しい選択ではありません。
私達が扱わなければならいハードウェア詳細に関する文書や情報は、
アーキテクチャの年齢にもかかわらず、すぐに見けたり理解できてりするものではありません。
(だから情報が沢山あるx86を使おう)

　OSは6週間のフルタイムワークで作成します。
実装は沢山の小さいステップを積み重ねていき、各ステップの終わりにOSの動作確認を手動でおこなっていきます。
このように段階的に繰り返し開発していくことで、最後に把握している正しい状態のコードから少しずつ変更するだけなので、
取り込んだバグの発見が簡単になります。私たちは、読者に同じ方法ですすめることを推奨します。

　6週間の開発の間、著者らが二人組（ペアプログラミング）になって大半のコードを1行1行書いていきました。
科学的に証明することは難しいが、この開発スタイルによって多くのバグをなんとか防ぎ上手くやってきたと信じています。

## <a name="the-reader">1.2 The Reader</a>

The reader of this book should be comfortable with UNIX/Linux, systems programming, the C language and computer systems in general (such as hexadecimal notation [3]). This book could be a way to get started learning those things, but it will be more difficult, and developing an operating system is already challenging on its own. Search engines and other tutorials are often helpful if you get stuck.

　この本の読者はUNIX/Linux、システムプログラミング、C言語、
そして一般的なコンピューターシステム（16進数表記など）の知識が求められます。
この本で上記のことを学ぶこともできますが、ともて難しいことですし、
それにOS開発だけでも既に挑戦的ことです。もしつまずいたときは、
検索エンジンや他のチュートリアルがしばしば役に立つでしょう。

## <a name="credits-thanks-and-acknowledgements"> 1.3 Credits, Thanks and Acknowledgements</a>

We’d like to thank the OSDev community [4] for their great wiki and helpful members, and James Malloy for his eminent kernel development tutorial [5]. We’d also like to thank our supervisor Torbjörn Granlund for his insightful questions and interesting discussions.

Most of the CSS formatting of the book is based on the work by Scott Chacon for the book Pro Git, http://progit.org/.

## <a name="contributors">1.4 Contributors</a>

We are very grateful for the patches that people send us. The following users have all contributed to this book:

* [alexschneider](https://github.com/alexschneider)
* [Avidanborisov](https://github.com/Avidanborisov)
* [nirs](https://github.com/nirs)
* [kedarmhaswade](https://github.com/kedarmhaswade)
* [vamanea](https://github.com/vamanea)
* [ansjob](https://github.com/ansjob)

## <a name="changes-and-corrections">1.5 Changes and Corrections</a>

This book is hosted on Github - if you have any suggestions, comments or corrections, just fork the book, write your changes, and send us a pull request. We’ll happily incorporate anything that makes this book better.


## <a name="issues-and-where-to-get-help">1.6 Issues and where to get help</a>

If you run into problems while reading the book, please check the issues on Github for help: https://github.com/littleosbook/littleosbook/issues.

## <a name="license">1.7 License</a>

All content is under the Creative Commons Attribution Non Commercial Share Alike 3.0 license, http://creativecommons.org/licenses/by-nc-sa/3.0/us/. The code samples are in the public domain - use them however you want. References to this book are always received with warmth.

# <a name="first-steps">2. First Steps</a>

Developing an operating system (OS) is no easy task, and the question “How do I even begin to solve this problem?” is likely to come up several times during the course of the project for different problems. This chapter will help you set up your development environment and booting a very small (and primitive) operating system.

## <a name="tools">2.1 Tools</a>
### <a name="quick-setup">2.1.1 Quick Setup</a>

We (the authors) have used Ubuntu [6] as the operating system for doing OS development, running it both physically and virtually (using the virtual machine VirtualBox [7]). A quick way to get everything up and running is to use the same setup as we did, since we know that these tools work with the samples provided in this book.

Once Ubuntu is installed, either physical or virtual, the following packages should be installed using`apt-get`:

```
    sudo apt-get install build-essential nasm genisoimage bochs bochs-sdl
```

### <a name="programming-languages">2.1.2 Programming Languages</a>

The operating system will be developed using the C programming language [8][9], using GCC [10]. We use C because developing an OS requires a very precise control of the generated code and direct access to memory. Other languages that provide the same features can also be used, but this book will only cover C.

The code will make use of one type attribute that is specific for GCC:

```
    __attribute__((packed))
```

This attribute allows us to ensure that the compiler uses a memory layout for a `struct` exactly as we define it in the code. This is explained in more detail in the next chapter.

Due to this attribute, the example code might be hard to compile using a C compiler other than GCC.

For writing assembly code, we have chosen NASM [11] as the assembler, since we prefer NASM’s syntax over GNU Assembler.

Bash [12] will be used as the scripting language throughout the book.

### <a name="host-operating-system">2.1.3 Host Operating System</a>

All the code examples assumes that the code is being compiled on a UNIX like operating system. All code examples have been successfully compiled using Ubuntu [6] versions 11.04 and 11.10.

### <a name="build-sysmte">2.1.4 Build System</a>

Make [13] has been used when constructing the Makefile examples.

### <a name="virtual-machine">2.1.5 Virtual Machine</a>

When developing an OS it is very convenient to be able to run your code in a virtual machine instead of on a physical computer, since starting your OS in a virtual machine is much faster than getting your OS onto a physical medium and then running it on a physical machine. Bochs [14] is an emulator for the x86 (IA-32) platform which is well suited for OS development due to its debugging features. Other popular choices are QEMU [15] and VirtualBox [7]. This book uses Bochs.

By using a virtual machine we cannot ensure that our OS works on real, physical hardware. The environment simulated by the virtual machine is designed to be very similar to their physical counterparts, and the OS can be tested on one by just copying the executable to a CD and finding a suitable machine.

## <a name="booting">2.2 Booting</a>

Booting an operating system consists of transferring control along a chain of small programs, each one more “powerful” than the previous one, where the operating system is the last “program”. See the following figure for an example of the boot process:

　OSは、PC制御を複数の小さなプログラムに順に移しながら起動している。
複数のプログラムは、順を追うごとに高機能になっていき、一番最後でOSプログラムが実行される。

```
BIOS -> GRUB -> GRUB2 -> OS
```
An example of the boot process. Each box is a program.

### <a name="bios">2.2.1 BIOS</a>

When the PC is turned on, the computer will start a small program that adheres to the Basic Input Output System (BIOS) [16] standard. This program is usually stored on a read only memory chip on the motherboard of the PC. The original role of the BIOS program was to export some library functions for printing to the screen, reading keyboard input etc. Modern operating systems do not use the BIOS’ functions, they use drivers that interact directly with the hardware, bypassing the BIOS. Today, BIOS mainly runs some early diagnostics (power-on-self-test) and then transfers control to the bootloader.

　PCの電源を入れた時に動き出す小さなプログラム。Basic Input Output Systemを省略したもの。
BIOSのプログラムはマザーボードに内蔵されたリードオンリーメモリーに保存されている。
BIOSプログラムの本来の役割は、スクリーンに出力したり、
キーボードの入力を読みこんだりするための入出力 ライブラリを外部へと提供することだった。
しかし、最近のOSではBIOSのライブラリには頼らず、BIOSを迂回してハードウェアと
直接やり取りするドライバーを使用している。そのため今日のBIOSは、
PC起動時の診断(Power on self test)をした後、ブートローダへと制御を移すのが主な役割だ。

### <a name="bootloader">2.2.2 Bootloader</a>

The BIOS program will transfer control of the PC to a program called a bootloader. The bootloader’s task is to transfer control to us, the operating system developers, and our code. However, due to some restrictions1 of the hardware and because of backward compatibility, the bootloader is often split into two parts: the first part of the bootloader will transfer control to the second part, which finally gives control of the PC to the operating system.

Writing a bootloader involves writing a lot of low-level code that interacts with the BIOS. Therefore, an existing bootloader will be used: the GNU GRand Unified Bootloader (GRUB) [17].

Using GRUB, the operating system can be built as an ordinary ELF [18] executable, which will be loaded by GRUB into the correct memory location. The compilation of the kernel requires that the code is laid out in memory in a specific way (how to compile the kernel will be discussed later in this chapter).

　BIOSプログラムは、Bootloaderと呼ばれるプログラムに制御を移す。
Bootloaderの仕事は、制御をOS開発者に移すことだ。
しかし、いくつかのハードウェアの制約や後方互換性により、
Bootloaderは２つに分担されることがおおい(GRUB1とGRUB2)。
一つ目は２つ目へと制御を移し、２つ目はOSへと制御を移していく。

　Bootloaderを1から作るということ、BIOSとやり取りするローレレベルのコードを大量に各必要があります。
そのため既存のブートローダを使用します。GRUB(GNU Grand Unified Bootloader)[[17]](#17)

　GRUBであれば、OSは通常のELF形式でビルドし、メモリーの正しい位置に配置しておけばよい。カーネルをコンパイルには、OSのコードをメモリにレイアウトする特別な方法が必要だ。（コンパイル方法については後に説明する。）

　ちなみに、ELFとはExecutable and Linkable Formatの略で、コンパイラが生成するオブジェクト、およびライブラリとリンクされた実行ファイルのファイルフォーマットのこと。a.outが一例。拡張子は「.o, .so, .elf. .app」などがある。

### <a name="the-operating-system"> 2.2.3 The Operating System</a>

GRUB will transfer control to the operating system by jumping to a position in memory. Before the jump, GRUB will look for a magic number to ensure that it is actually jumping to an OS and not some random code. This magic number is part of the multiboot specification [19] which GRUB adheres to. Once GRUB has made the jump, the OS has full control of the computer.

　GRUBはメモリのある位置にジャンプすることで、OSに制御を移します。
GRUBは、OSに確実にジャンプするためのマジックナンバーを探します。
このマジックナンバーはマルチブート仕様(Multiboot specification[19](#19)）に準じたものです。
ひとたびGRUBがジャンプしてしまえば、OSはコンピュータの全制御権を得ることになります。

## <a name="hello-cafebabe">2.3 Hello Cafebabe</a>

This section will describe how to implement of the smallest possible OS that can be used together with GRUB. The only thing the OS will do is write 0xCAFEBABE to the eax register (most people would probably not even call this an OS).

　このセクションでは、GRUBで呼び出すことが可能な最小なOSの実装方法について述べていきます。
このOSは、EAXレジスタにOxCAFEBABEと書き込むだけのOSです。
（たいての人は、とてもOSとは思えないようなものです。）

### <a name="compiling-the-operating-system">2.3.1 Compiling the Operating System</a>

This part of the OS has to be written in assembly code, since C requires a stack, which isn’t available (the chapter “Getting to C” describes how to set one up). Save the following code in a file called loader.s:

　OSのこの部分では、アセンブリーコードで書かなければならなりません。
ちなみにC言語の処理を呼び出すにはカーネルスタックの設定が必要ですが、この章ではCの処理は出てこないので不要です。
（[Getting to C](#getting-to-c)の章でカーネルスタックの設定方法を記述しています。）
以下のソースコーどをloader.sというファイル名で保存しましょう。

``` ini
global loader                   ; the entry symbol for ELF

MAGIC_NUMBER equ 0x1BADB002     ; define the magic number constant
FLAGS        equ 0x0            ; multiboot flags
CHECKSUM     equ -MAGIC_NUMBER  ; calculate the checksum
                                ; (magic number + checksum + flags should equal 0)

section .text:                  ; start of the text (code) section
align 4                         ; the code must be 4 byte aligned
  dd MAGIC_NUMBER               ; write the magic number to the machine code,
  dd FLAGS                      ; the flags,
  dd CHECKSUM                   ; and the checksum

loader:                         ; the loader label (defined as entry point in linker script)
  mov eax, 0xCAFEBABE           ; place the number 0xCAFEBABE in the register eax
.loop:
  jmp .loop                     ; loop forever
```

The only thing this OS will do is write the very specific number 0xCAFEBABE to the eax register. It is very unlikely that the number 0xCAFEBABE would be in the eax register if the OS did not put it there.

The file loader.s can be compiled into a 32 bits ELF [18] object file with the following command:

このOSがすることは、0xCAFEBABEという特定の番号をeaxレジスターに書き込むだけです。
もしOSが書き込まなければ0xCAFEBABEという数字がeaxレジスターにあることはまずないでしょう。
（特殊な数字なので自然に書き込まれることはない）

loader.sファイルは以下のコマンドで32bit ELFオブジェクトファイルにコンパイルされます。

```
nasm -f elf32 loader.s
```

###<a name="linking-the-kernel"> 2.3.2 Linking the Kernel</a>

The code must now be linked to produce an executable file, which requires some extra thought compared to when linking most programs. We want GRUB to load the kernel at a memory address larger than or equal to 0x00100000 (1 megabyte (MB)), because addresses lower than 1 MB are used by GRUB itself, BIOS and memory-mapped I/O. Therefore, the following linker script is needed (written for GNU LD [20]):

　上記のコード(loader.o 機械語のコード)は、実行可能なファイルを作るするために
リンク処理する必要があります。それは、ふつうのプログラムをリンクする時と比べて、
いくつか別のことを考慮する必要があります。
我々は1MB以上(0x00100000)のメモリアドレスにカーネルをロードするGRUBを必要としています。
なぜなら、1MBより小さいアドレスはGRUB自身、BIOSそしてメモリマップドI/Oによって
使われるためです。したがって、以下の様なLinkerスクリプトが必要になります。
（このスクリプトはGNU LDにしたがって書かれました[[20]](#20)）

```
ENTRY(loader)                /* the name of the entry label */

SECTIONS {
    . = 0x00100000;          /* the code should be loaded at 1 MB */

    .text ALIGN (0x1000) :   /* align at 4 KB */
    {
        *(.text)             /* all text sections from all files */
    }

    .rodata ALIGN (0x1000) : /* align at 4 KB */
    {
        *(.rodata*)          /* all read-only data sections from all files */
    }

    .data ALIGN (0x1000) :   /* align at 4 KB */
    {
        *(.data)             /* all data sections from all files */
    }

    .bss ALIGN (0x1000) :    /* align at 4 KB */
    {
        *(COMMON)            /* all COMMON sections from all files */
        *(.bss)              /* all bss sections from all files */
    }
}
```
Save the linker script into a file called link.ld. The executable can now be linked with the following command:
このLinkerスクリプトはlink.ldというファイルで保存します。そして実行可能ファイルを以下のコマンドでリンクします

```
ld -T link.ld -melf_i386 loader.o -o kernel.elf
```
The final executable will be called kernel.elf.
最終的な実行可能ファイルはkernel.elfと名づけます。


### <a name="obtaining-grub">2.3.3 Obtaining GRUB</a>

The GRUB version we will use is GRUB Legacy, since the OS ISO image can then be generated on systems using both GRUB Legacy and GRUB 2. More specifically, the GRUB Legacy stage2_eltorito bootloader will be used. This file can be built from GRUB 0.97 by downloading the source from ftp://alpha.gnu.org/gnu/grub/grub-0.97.tar.gz. However, the configure script doesn’t work well with Ubuntu [21], so the binary file can be downloaded from http://littleosbook.github.com/files/stage2_eltorito. Copy the file stage2_eltorito to the folder that already contains loader.s and link.ld.


　GRUB LegacyとGRUB2のどちらでもOSのISOイメージを作成できるのでが、今回私達はGRUB Legacyを使用します。
より詳しくいうと、GRUB Legacy の stage2_eltorito bootloaderを使用します。
(ftp:://alpha.gnu.org/gnu/grub/grub-0.97.tar.gz)にあるソースコードから、
GRUB0.97を使用すればこのファイルを生成出来ます。
しかし、configureスクリプトがUbuntui[[21]](#21)だとうまく動作しないので、
バイナリファイルを以下の場所からダウンロードできます。
(http://littleosbook.github.com/files/stage2_eltorito) 
stage2_eltoritoをloader.sとlink.ldがあるフォルダにコピーしてください。

###<a name="building-an-iso-image">2.3.4 Building an ISO Image</a>

The executable must be placed on a media that can be loaded by a virtual or physical machine. In this book we will use ISO [22] image files as the media, but one can also use floppy images, depending on what the virtual or physical machine supports.

We will create the kernel ISO image with the program genisoimage. A folder must first be created that contains the files that will be on the ISO image. The following commands create the folder and copy the files to their correct places:


　実行可能ファイルは、仮想マシンや実マシンがロード可能なメディア上に置かなければならない。
この本ではメディアの代わりにISO[[22]](#22)イメージを使用しますが、フロッピーイメージを使っても可能です。
使用する仮想マシン、実マシンがどのメディアをサポートしているに依存する。

　genisoimageコマンドを使って、Kernel ISOイメージをつくります。
まずはじめにISOイメージ上に置くファイルを含んだフォルダを作っていきます。
以下のコマンドでフォルダーを作成し、ファイルを正しい場所にコピーしてください。

``` bash
mkdir -p iso/boot/grub            #create the folder structure
cp stage2_eltorito iso/boot/grub  #copy the bootloader
cp kernel.elf iso/boot/           #copy the kernel
```
A configuration file menu.lst for GRUB must be created. This file tells GRUB where the kernel is located and configures some options:
　GRUBの設定ファイルmenu.lstをつくります。
このファイルはGRUBにカーネルの場所と、オプションを伝えます。

``` no-highlight
default=0
timeout=0

title os
kernel /boot/kernel.elf
```
Place the file menu.lst in the folder iso/boot/grub/. The contents of the iso folder should now look like the following figure:
　menu.lstファイルをiso/boot/grubに置きます
isoフォルダの中身は以下の図のようにしてください。

``` no-highlight
iso
|-- boot
 |-- grub
 ||-- menu.lst
 ||-- stage2_eltorito
 |-- kernel.elf
```
The ISO image can then be generated with the following command:

　ISOイメージは以下のコマンドで生成できます。

``` bash
genisoimage -R                              \
            -b boot/grub/stage2_eltorito    \
            -no-emul-boot                   \
            -boot-load-size 4               \
            -A os                           \
            -input-charset utf8             \
            -quiet                          \
            -boot-info-table                \
            -o os.iso                       \
            iso
```

For more information about the flags used in the command, see the manual for genisoimage.

The ISO image os.iso now contains the kernel executable, the GRUB bootloader and the configuration file.

コマンドの各フラグの意味については、genisoimageのマニュアルをみてください。

ISOイメージのos.isoは実行可能なkernelプログラムとGRUBブートローダと設定ファイルを含んでいます。

### <a name="running-bochs">2.3.5 Running Bochs</a>

Now we can run the OS in the Bochs emulator using the os.iso ISO image. Bochs needs a configuration file to start and an example of a simple configuration file is given below:

　ISOイメージのos.isoを使用して、Bochsエミュレーター上でOSを走らせます。
Bochsは実行するための設定ファイルが必要なので、以下のような簡単な設定例を紹介します。

```
megs:            32
display_library: sdl
romimage:        file=/usr/share/bochs/BIOS-bochs-latest
vgaromimage:     file=/usr/share/bochs/VGABIOS-lgpl-latest
ata0-master:     type=cdrom, path=os.iso, status=inserted
boot:            cdrom
log:             bochslog.txt
clock:           sync=realtime, time0=local
cpu:             count=1, ips=1000000
```

You might need to change the path to romimage and vgaromimage depending on how you installed Bochs. More information about the Bochs config file can be found at Boch’s website [23].

If you saved the configuration in a file named bochsrc.txt then you can run Bochs with the following command:

romimageとvgaromimageはBochsをどうやってインストールしたかによって変更する必要があります。
(Ubuntuでapt-getを使用していれば上記のままで問題ない)
Bochsの設定ファイルについてもっと情報が欲しいのであれば、Bochsのウェブサイトをみるとよいでしょう。[[23]](#23)

設定ファイルをbochsrc.txtという名前で保存したら、以下のコマンドでBochsを実行して下さい。

``` bash
bochs -f bochsrc.txt -q
```

The flag -f tells Bochs to use the given configuration file and the flag -q tells Bochs to skip the interactive start menu. You should now see Bochs starting and displaying a console with some information from GRUB on it.

After quitting Bochs, display the log produced by Boch:

　-f は、指定した設定ファイルをBochsに読み込ませるフラグです。
-q は、Bochs起動時のインタラクティブ開始メニューを飛ばすフラグです。
bochsコマンドを実行するとBochsが開始され、コンソール上にGRUBの情報が表示されます。

　Bochsを終了したあと、以下のコマンドでBochsが生成したログを表示します。

``` bash
cat bochslog.txt
```

You should now see the contents of the registers of the CPU simulated by Bochs somewhere in the output. If you find RAX=00000000CAFEBABE or EAX=CAFEBABE (depending on if you are running Bochs with or without 64 bit support) in the output then your OS has successfully booted!

　実行結果の出力どこかにBochsがシミュレートしたCPUのレジスタの内容が見て取れます。
RAX=00000000CAFEBABE もしくは EAX=CAFEBABE（Bochsが64bitサポートかそうでないかで変わる）
を出力から見つけたなら、あなたのOSは無事に起動出来ていたことになります。

## <a name="furtuer-reading">2.4 Further Reading</a>
- [Gustavo Duertes has written an in-depth article about what actually happens when a x86 computer boots up](http://duartes.org/gustavo/blog/post/how-computers-boot-up)
- [Gustavo continues to describe what the kernel does in the very early stages at](http://duartes.org/gustavo/blog/post/kernel-boot-process)
- [The OSDev wiki also contains a nice article about booting an x86 computer](http://wiki.osdev.org/Boot_Sequence)

# <a name="getting-to-c">3 Getting to C</a>

This chapter will show you how to use C instead of assembly code as the programming language for the OS. Assembly is very good for interacting with the CPU and enables maximum control over every aspect of the code. However, at least for the authors, C is a much more convenient language to use. Therefore, we would like to use C as much as possible and use assembly code only where it make sense.

　この章ではOSの開発言語として、アセンブラの代わりにC言語使うにはどうしたらよいか説明していきます。
アセンブラ言語は、CPUとやり取りするのに最も良い言語ですし、プログラムのあらゆる側面において最大限の制御を可能にします。
しかしながら、少なとも著者らは、C言語のほうが使い勝手のよい言語だと思っています。
したがって我々は可能な限りC言語をつかい、意味がある箇所ではアセンブラを使用したいと思います。

## <a name="setting-up-a-stack">3.1 Setting Up a Stack</a>

One prerequisite for using C is a stack, since all non-trivial C programs use a stack. Setting up a stack is not harder than to make the esp register point to the end of an area of free memory (remember that the stack grows towards lower addresses on the x86) that is correctly aligned (alignment on 4 bytes is recommended from a performance perspective).

　C言語を用いるための前提条件の一つがスタックです。
なぜなら、全ての些細ではないCプログラムは、スタックを使用するからです。
スタックの設定のほうが、4byteに揃えられた空きメモリ空間の終端アドレスをESPレジスタで指させることよりも簡単です。
(x86ではスタックは下位のアドレスにむかって伸ることを覚えておいてください。)
(4byteに揃えることはパフォーマンスの点で推奨されています)
(ちなみにESPレジスタとは、スタックの一番のアドレスを指し続けるのが役割です。)

We could point esp to a random area in memory since, so far, the only thing in the memory is GRUB, BIOS, the OS kernel and some memory-mapped I/O. This is not a good idea - we don’t know how much memory is available or if the area esp would point to is used by something else. A better idea is to reserve a piece of uninitialized memory in the bss section in the ELF file of the kernel. It is better to use the bss section instead of the data section to reduce the size of the OS executable. Since GRUB understands ELF, GRUB will allocate any memory reserved in the bss section when loading the OS.

　これまでメモリ内にあったのはGRUB,BIOS,OSカーネルとメモリマップドI/Oだけだったが、
(スタックの登場によって)ESPレジスタが、メモリ内をランダムに指す可能性がでてきます。
これはいいアイディアではありません。
どのくらいメモリに空きがあるのか分からないし、もしESPが指すアドレスが既に使われたらどうなるでしょう。
そこでカーネルのELFファイルで、メモリのbss(Block Started by Symbol)セクションの
未初期化領域の一部を予め確保しておくのが、より良いアイディアだと思います。
**OSの実行可能ファイルのサイズを減らすため、dataセクションの変わりにbssセクションを使用したほうが良いです。
GRUBはELFファイルを理解しているので、OSを読み込んでいる時にGRUBは
bssセクション内で予め確保されたメモリを確保しにいきます。**

The NASM pseudo-instruction resb [24] can be used to declare uninitialized data:

　NASMの擬似命令(高級言語で記述された命令。機械語ではない。)resb[[24]](#24)
は、未初期化のデータを宣言するために使われます。

``` gnuassembler
KERNEL_STACK_SIZE equ 4096                  ; size of stack in bytes

section .bss
align 4                                     ; align at 4 bytes
kernel_stack:                               ; label points to beginning of memory
    resb KERNEL_STACK_SIZE                  ; reserve stack for the kernel
```
There is no need to worry about the use of uninitialized memory for the stack, since it is not possible to read a stack location that has not been written (without manual pointer fiddling). A (correct) program can not pop an element from the stack without having pushed an element onto the stack first. Therefore, the memory locations of the stack will always be written to before they are being read.

　スタックが、メモリの未初期化領域を使うことについては、何も心配する必要はありません。
(初期化されていない領域だから、何か変な値をとってきてしまうのではないか、という心配は不要)
なぜなら、何も書き込まれていないスタックの場所を読み込むことは不可能だからです。
（ポインタでアドレスを直接参照したりしなければの話。）
正しいプログラムは、はじめにスタックに何か一つ要素が入らなければ、スタックから要素を取り出せないようになっています。
それゆえスタックのメモリ空間は、読まれる前にかならず何か書き込まれているでしょう。

The stack pointer is then set up by pointing esp to the end of the kernel_stack memory:

　スタックポインタは、ESPレジスタが、kernel_stackラベルのメモリの終端のアドレスを指し他状態でセットアップされます。

```
mov esp, kernel_stack + KERNEL_STACK_SIZE   ; point esp to the start of the
                                            ; stack (end of memory area)
```

## 3.2 Calling C Code From Assembly
The next step is to call a C function from assembly code. There are many different conventions for how to call C code from assembly code [25]. This book uses the cdecl calling convention, since that is the one used by GCC. The cdecl calling convention states that arguments to a function should be passed via the stack (on x86). The arguments of the function should be pushed on the stack in a right-to-left order, that is, you push the rightmost argument first. The return value of the function is placed in the eax register. The following code shows an example:

　次のステップでは、アセンブラのコードからC言語関数の呼び出をします
アセンブラのコードからCのコードの呼び出す方法は、様々な習慣があります[[25]](#25)。
この本では、GCCで使用できるもの一つであるcdecl callingという慣例を使用します。
cdecl callingは、(x86上の)スタックによってもたらされるべき関数の引数を宣言します。
関数の引数たちは右から左の順(一番右の引数を最初にスタックにPushする)でスタックに入るべきでしょう。
関数の戻り値は、EAXレジスタが指し示している場所です。以下のサンプルコードです。

``` c
/* The C function */
int sum_of_three(int arg1, int arg2, int arg3) {
    return arg1 + arg2 + arg3;
}
```
``` gnuassembler
; The assembly code
external sum_of_three   ; the function sum_of_three is defined elsewhere

push dword 3            ; arg3
push dword 2            ; arg2
push dword 1            ; arg1
call sum_of_three       ; call the function, the result will be in eax
```

### 3.2.1 Packing Structs
In the rest of this book, you will often come across "configuration bytes" that are a collection of bits in a very specific order. Below follows an example with 32 bits:

以降、しばしば非常に特殊な並びをしたビットの集合"configuration bytes"に出くわすでしょう。
以下32ビットの例です。

```
Bit:     | 31     24 | 23          8 | 7     0 |
Content: | index     | address       | config  |
```

Instead of using an unsigned integer, unsigned int, for handling such configurations, it is much more convenient to use "packed structures":

このような設定情報を扱い場合、unsigned integerを使用する代わりに
"packed structures"とう構造体を使用するほうがが非常に便利です。

``` c
struct example {
    unsigned char config;   /* bit 0 - 7   */
    unsigned short address; /* bit 8 - 23  */
    unsigned char index;    /* bit 24 - 31 */
};
```

When using the struct in the previous example there is no guarantee that the size of the struct will be exactly 32 bits - the compiler can add some padding between elements for various reasons, for example to speed up element access or due to requirements set by the hardware and/or compiler. When using a struct to represent configuration bytes, it is very important that the compiler does not add any padding, because the struct will eventually be treated as a 32 bit unsigned integer by the hardware. The attribute packed can be used to force GCC to not add any padding:

上の例であげた構造体を使用すると、構造体の合計サイズが32bit丁度になる保証がありません。コンパイラーが要素の間をpadding
たとえば、要素へのアクセスを速くするため、もしくはハードウェアやコンパイラーの制限によるものがあります。

``` c
struct example {
     unsigned char config;   /* bit 0 - 7   */
     unsigned short address; /* bit 8 - 23  */
     unsigned char index;    /* bit 24 - 31 */
} __attribute__((packed));
```

Note that __attribute__((packed)) is not part of the C standard - it might not work with all C compilers.





#<a name="references"> 14.4 References</a>

<a name="1">[1] Andrew Tanenbaum, 2007\. *Modern operating systems, 3rd edition*. Prentice Hall, Inc.,

<a name="2">[2] *The royal institute of technology*, [http://www.kth.se](http://www.kth.se/),

<a name="3">[3] Wikipedia, *Hexadecimal*, <http://en.wikipedia.org/wiki/Hexadecimal>,

<a name="4">[4] OSDev, *OSDev*, [http://wiki.osdev.org/Main\_Page](http://wiki.osdev.org/Main_Page),

<a name="5">[5] James Molloy, *James m’s kernel development tutorial*, [http://www.jamesmolloy.co.uk/tutorial\_html/](http://www.jamesmolloy.co.uk/tutorial_html/),

<a name="6">[6] Canonical Ltd, *Ubuntu*, <http://www.ubuntu.com/>,

<a name="7">[7] Oracle, *Oracle vM virtualBox*, <http://www.virtualbox.org/>,

<a name="8">[8] Dennis M. Ritchie Brian W. Kernighan, 1988\. *The c programming language, second edition*. Prentice Hall, Inc.,

<a name="9">[9] Wikipedia, *C (programming language)*, [http://en.wikipedia.org/wiki/C\_(programming\_language)](http://en.wikipedia.org/wiki/C_(programming_language)),

<a name="10">[10] Free Software Foundation, *GCC, the gNU compiler collection*, <http://gcc.gnu.org/>,

<a name="11">[11] NASM, *NASM: The netwide assembler*, <http://www.nasm.us/>,

<a name="12">[12] Wikipedia, *Bash*, [http://en.wikipedia.org/wiki/Bash\_%28Unix\_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29),

<a name="13">[13] Free Software Foundation, *GNU make*, <http://www.gnu.org/software/make/>,

<a name="14">[14] Volker Ruppert, *bochs: The open souce iA-32 emulation project*, <http://bochs.sourceforge.net/>,

<a name="15">[15] QEMU, *QEMU*, [http://wiki.qemu.org/Main\_Page](http://wiki.qemu.org/Main_Page),

<a name="16">[16] Wikipedia, *BIOS*, <https://en.wikipedia.org/wiki/BIOS>,

<a name="17">[17] Free Software Foundation, *GNU gRUB*, <http://www.gnu.org/software/grub/>,

<a name="18">[18] Wikipedia, *Executable and linkable format*,[http://en.wikipedia.org/wiki/Executable\_and\_Linkable\_Format](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format),

<a name="19">[19] Free Software Foundation, *Multiboot specification version 0.6.96*, [http://www.gnu.org/software/ grub/manual/multiboot/multiboot.html](http://www.gnu.org/software/%20%20%20%20%20%20%20%20%20%20%20grub/manual/multiboot/multiboot.html),

<a name="20">[20] GNU, *GNU binutils*, <http://www.gnu.org/software/binutils/>,

<a name="21">[21] Lars Nodeen, *Bug \#426419: configure: error: GRUB requires a working absolute objcopy*,<https://bugs.launchpad.net/ubuntu/+source/grub/+bug/426419>,

<a name="22">[22] Wikipedia, *ISO image*, [http://en.wikipedia.org/wiki/ISO\_image](http://en.wikipedia.org/wiki/ISO_image),

<a name="23">[23] Bochs, *bochsrc*, <http://bochs.sourceforge.net/doc/docbook/user/bochsrc.html>,

<a name="24">[24] NASM, *RESB and friends: Declaring uninitialized data*, <http://www.nasm.us/doc/nasmdoc3.htm>,

<a name="25">[25] Wikipedia, *x86 calling conventions*, [http://en.wikipedia.org/wiki/X86\_calling\_conventions](http://en.wikipedia.org/wiki/X86_calling_conventions),

<a name="26">[26] Wikipedia, *Framebuffer*, <http://en.wikipedia.org/wiki/Framebuffer>,

<a name="27">[27] Wikipedia, *VGA-compatible text mode*, [http://en.wikipedia.org/wiki/VGA-compatible\_text\_mode](http://en.wikipedia.org/wiki/VGA-compatible_text_mode),

<a name="28">[28] Wikipedia, *ASCII*, <https://en.wikipedia.org/wiki/Ascii>,

<a name="29">[29] OSDev, *VGA hardware*, [http://wiki.osdev.org/VGA\_Hardware](http://wiki.osdev.org/VGA_Hardware),

<a name="30">[30] Wikipedia, *Serial port*, [http://en.wikipedia.org/wiki/Serial\_port](http://en.wikipedia.org/wiki/Serial_port),

<a name="31">[31] OSDev, *Serial ports*, [http://wiki.osdev.org/Serial\_ports](http://wiki.osdev.org/Serial_ports),

<a name="32">[32] WikiBooks, *Serial programming/8250 uART programming*,[http://en.wikibooks.org/wiki/Serial\_Programming/ 8250\_UART\_Programming](http://en.wikibooks.org/wiki/Serial_Programming/%20%20%20%20%20%208250_UART_Programming),

<a name="33">[33] Intel, *Intel 64 and iA-32 architectures software developer’s manual vol. 3A*,[http://www.intel.com/content/ www/us/en/architecture-and-technology/64-ia-32-architectures-software-developer-vol-3a-part-1-manual.html/](http://www.intel.com/content/www/us/en/architecture-and-technology/64-ia-32-architectures-software-developer-vol-3a-part-1-manual.html/),

<a name="34">[34] NASM, *Multi-line macros*, [http://www.nasm.us/doc/nasmdoc4.html\#section-4.3](http://www.nasm.us/doc/nasmdoc4.html#section-4.3),

<a name="35">[35] SIGOPS, *i386 interrupt handling*, [http://www.acm.uiuc.edu/sigops/roll\_your\_own/i386/irq.html](http://www.acm.uiuc.edu/sigops/roll_your_own/i386/irq.html),

<a name="36">[36] Andries Brouwer, *Keyboard scancodes*, <http://www.win.tue.nl/>,

<a name="37">[37] Steve Chamberlain, *Using ld, the gNU linker*, [http://www.math.utah.edu/docs/info/ld\_toc.html](http://www.math.utah.edu/docs/info/ld_toc.html),

<a name="38">[38] OSDev, *Page frame allocation*, [http://wiki.osdev.org/Page\_Frame\_Allocation](http://wiki.osdev.org/Page_Frame_Allocation),

<a name="39">[39] OSDev, *Programmable interval timer*, [http://wiki.osdev.org/Programmable\_Interval\_Timer](http://wiki.osdev.org/Programmable_Interval_Timer),

---

1. The bootloader must fit into the *master boot record* (MBR) boot sector of a hard drive, which is only 512 bytes large.[↩](#fnref1)
