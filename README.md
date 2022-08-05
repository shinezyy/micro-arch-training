# micro-arch-training
How to make undergraduates or new graduates ready for advanced computer architecture research or modern CPU design.
本项目的目的是让本科生或新入学的研究生迅速地可以参加体系结构研究或参与高性能处理器开发。

# Off-topic

尽管我们主要在讨论计算机体系结构，但是我们强烈推荐大家扎实地学习好其他基础课程，例如计算机系统基础、操作系统、编译原理。
这些课程对理解微体系结构设计、帮助完成体系结构相关实验有非常大的帮助。
例如CPU中的寄存器重命名和编译器的寄存器分配其实互为“逆过程”，编译原理可以为你学习乱序执行提供一种全新的视角。
再例如，操作系统的中断返回和启动相关代码也可以用来制作体系结构研究用的Checkpoint。

## Introduction to Computer System

这部分的课程学习建议读CSAPP那本书，实验推荐做[NEMU Programming Assignment](https://nju-projectn.github.io/ics-pa-gitbook/ics2022/)。
这个实验让写一个可以启动简单操作系统、运行仙剑奇侠传的模拟器。

## Operating System

很幸运，我们找到了质量比较高的录制好的中文操作系统课程[南京大学 “操作系统：设计与实现” (蒋炎岩)](https://www.bilibili.com/video/BV1HN41197Ko)。
课程实验，我们推荐做[MIT 6.828的实验](https://pdos.csail.mit.edu/6.828/2021/xv6.html)，这个实验让写一个Non-trivial的操作系统。

## Compiler

我们暂时没有找到合适的中文公开课，所以推荐[Stanford CS 143](https://www.youtube.com/watch?v=SNWHmnWzJAI&list=PLoCMsyE1cvdUZRe1udlyjpzTww1U5olL2)
我们也推荐做[CS 143的实验课Cool Compiler](https://github.com/search?q=cool+compiler+lab)，因为实验材料需要从内网下载，所以我们只好在Github搜一个来做。
这个实验让写一个语法较为Fancy的编译器，然后生成汇编代码，可选做一些优化。

最后，因为如果有高质量的中文公开课或者更好的实验素材，欢迎大家可以发PR给我们推荐一下。我们希望以上的每门课都有一门高质量的中文公开课+一门高质量的英文公开课+高质量的实验课。

# Computer Architecture

现在我们回到正题——计算机体系结构。根据我们的了解，目前很多（高级）体系结构课都不够深入，无法保证学生在完成课程之后就能进行相关研究。
本项目希望弥补这一空缺，培养面向体系结构研究或者高性能处理器开发的能力，包括理论知识和实践能力。

首先，我们继续推荐公开课：[Onur Mutlu的体系结构课](https://www.bilibili.com/video/BV1PT4y1M7gM?p=1)
或者[David Wentzlaff的体系结构课](https://www.bilibili.com/video/av93575643)。
这类课程都适合本科生入门看，但是距离做研究还有一段距离。

同时我们还看到有[Onur Mutlu的高级体系结构课](https://www.bilibili.com/video/BV1Vf4y1i7YG)这样的面向研究生的体系结构课程。
这类课程非常有深度，但是有时候和授课老师的研究方向强相关，比如Mutlu现在主要做Memory，所以这门课主要在讲Memory。
我们发现[UWisc的CS752](https://pages.cs.wisc.edu/~sinclair/courses/cs752/fall2020/includes/schedule.html)在各个方面较为均衡，
因此我们会以CS752为骨架，主要使用CS752的slides，同时推荐相关论文，然后我们会设计一些课程实验帮助大家熟悉研究工具。

## Slides

WIP...

## Papers

### 乱序执行

[MIPS R10000](https://pages.cs.wisc.edu/~markhill/restricted/ieeemicro96_r10000.pdf)

[SMT](https://pages.cs.wisc.edu/~markhill/restricted/isca96_smt.pdf)

[Complexity-effective superscalar processors](http://www.eecs.harvard.edu/cs146-246/isca.complexity.pdf)

### 性能测量与分析

[SimPoint ASPLOS-2002](https://cseweb.ucsd.edu/~calder/papers/ASPLOS-02-SimPoint.pdf)

[SMARTS](https://infoscience.epfl.ch/record/135578/files/isca03_smarts.pdf)

[Per-Thread Cycle Accounting in SMT Processors](https://www.researchgate.net/profile/Stijn-Eyerman/publication/220938808_Per-Thread_Cycle_Accounting_in_SMT_Processors/links/53ea27980cf2fb1b9b6765dd/Per-Thread-Cycle-Accounting-in-SMT-Processors.pdf)

### 分支预测

[PPM for branch prediction](https://dl.acm.org/doi/pdf/10.1145/248209.237171)

[TAGE](https://hal.inria.fr/hal-03408381/document)


## Basics

### Entrance-level knowledge on computer ~science~

作为一个做计算机系统或者体系结构的人，有一些入门级的知识需要补充，
最起码我们应该比百度贴吧里的中学生更了解计算机。

#### Context switch

记住一件事：不要在N核服务器上运行大于N个长时间任务。如果不知道为什么，建议重修操作系统。

#### SMT Contention

大部分AMD和Intel的服务器是启用了SMT功能的，这会导致它看上去有256核，实际上只有128个物理核。
共享同一个物理核心的物理线程（HART）之间会相互干扰对方的性能，这个干扰可能非常大，甚至可能超过50%。
所以，我的建议是

- 当有更多服务器可以用的时候，不要把HART挤在同一个物理核上，让服务器CPU只占用50%最好
- 当非要用SMT功能的时候
  - 确保自己更需要吞吐率而不是time to return，尤其是跑实验的时候
  - 确保自己做过Profiling，知道性能干扰小于50%

关于SMT，应该读上面提到过的 SMT入门论文。
如果对SMT的性能干扰感兴趣，我厚着脸皮推荐我们的论文[QoSMT](https://dl.acm.org/doi/10.1145/3330345.3330364)。

#### NUMA

NUMA 的问题讨论很多了，自己看看wiki吧。
关键在于在服务器上学会使用numactl，避免把process分配在node0上，而memory在node1。

#### NUCA

NUCA是一个比NUMA更罕见的概念，但是我们作为研究体系结构的人，也应该搞清楚。
为什么会有NUCA？
[An adaptive, non-uniform cache structure for wire-delay dominated on-chip cachesNon-uniform cache structure](https://dl.acm.org/doi/abs/10.1145/605397.605420)

NUCA和我有什么关系，他真的商用了吗？
[看一看AnandTech这篇文章](https://www.anandtech.com/show/16214/amd-zen-3-ryzen-deep-dive-review-5950x-5900x-5800x-and-5700x-tested/5)
Emmm，又是别人搞测评的都知道的东西，研究体系结构也该弄清楚吧。

对于NUCA，我的建议是：
- 如果使用AMD服务器，并且有数据交换较多的多线程任务，让他们位于同一个CCX
- 怎么让他们位于同一个CCX呢？
  - numactl可以控制任务所处的CPU
  - Linux上序号相邻的4/8/16个核经常位于同一个CCX，具体看型号。你也可以直接做profiling。


### Basic security

关于密钥
- 建议用私钥访问服务器和Git
- 你放在服务器上的私钥是有风险的，建议把在服务器上的私钥用密码保护起来
- 原则上，服务器都应该禁止用密码登录

### Version control

Tool Task:
学习以下命令的使用：

```
git checkout deadbeef
git checkout path/to/a/file

git format-patch
git apply
git apply --check
git am

git rebase -i

git rm
git rm --cached
```
当你搞了一串乱七八糟的git commit history的时候，以上命令可以帮助你，并且大部分情况下，他们就够了

如果要参与开源项目开发，你或许还需要掌握这些命令：

```
git merge xxx
git rebase xxx
git cherry-pick xxx..yyy
git commit --fixup
```
可以参考(一位同学写的GIT学习笔记)[https://zhuanlan.zhihu.com/p/526826127]

记住：
- 不要用`git add .`，最好用`git add -p`
- 99%的情况，不要track log文件
- 99%的情况，不要track binary文件

## Simulator - GEM5

这里是上手用GEM5的入门训练

### Build GEM5
WIP...

### Configure GEM5

Tool Task:
配置GEM5的Cache如下：
`16 kB L1 I-Cache + 16 kB L1 D-Cache + 256kB L2 Cache + 2M L3 Cache; L2 and L3 Mostly-exclusive; Writeback clean`
或许你不知道什么是Mostly-exclusive和Writeback clean，你需要主动去搜索学习、阅读代码。

把[这里编译好的Coremark](#coremark)作为payload，运行GEM5，采集数据。

### Modify GEM5

#### Compile a broken GEM5

尝试使这个无法编译的GEM5项目通过编译：[gem5-quiz](https://github.com/OpenXiangShan/GEM5/tree/gem5-test-1)

提示：其实这是一道C++题目。

#### GEM5 debug flags

#### GEM5 statistics

首先，需要学习GEM5的数据统计体系，了解 Stats::Scalar, Stats::Vec, Stats::Formula的用法，具体可以用grep读一读代码。
然后增加一些性能计数器，
- 用Stats::Vec统计每个周期发射的load指令的条数分布
- 用Stats::Vec统计发射的Load指令和发射的Store指令的比例

#### Add new configurable parameter 

"https://www.gem5.org/documentation/learning_gem5/part2/events/"

#### Event-driven programming

Tool task:
在退出时Dump cache中所有的line的地址和内容，参考[Event-driven programming](https://www.gem5.org/documentation/learning_gem5/part2/events/)。

Research training task:
在退出时Dump cache中所有的line的地址和内容，按照`Least Important`的顺序导出。例如，当是`LRU`替换算法时，用`MRU`序导出。

#### Batch running

Tool Task:
利用[BatchTaskTemplate](https://github.com/shinezyy/DirtyStuff.git)批量运行GEM5。
具体地，拷贝一份`gem5tasks/restore_gcpt.py`，仔细阅读注释，修改里面的配置，把GEM5批量跑起来。

#### Collecting statistics

#### Collecting batch-running statistics

WIP...

## Simulator - NEMU

### Take Checkpoints (Generic RISC-V Checkpoints)
WIP...

## Simulator - QEMU
暂时鸽着

## Verilator-Xiangshan
暂时鸽着

## Workloads

这里是制作研究用的Workload的入门训练

### Coremark

编译一个RISC-V指令集的Coremark

#### 编译基于newlib的Coremark

Debug Training Task:

使用[Boom提供Coremark编译脚本](https://github.com/riscv-boom/riscv-coremark.git)编译Coremark，你可能需要自己安装[RISC-V gnu toolchian](https://github.com/riscv-collab/riscv-gnu-toolchain)。

并用GEM5运行：
```./build/RISCV/gem5.opt ./configs/example/se.py -c /path/to/coremark.riscv```
可能会发现Coremark没有输出，出了什么问题？
学习者需要自己找到答案，记录猜测、验证猜测的过程，这个过程非常重要。
可能用到的工具：
- [GEM5 statistics](#gem5-statistics)
- [GEM5 debug flags](#gem5-debug-flags)
- QEMU / NEMU

####
使用[AM裸机环境](https://github.com/OpenXiangShan/nexus-am)编译裸机Coremark，参考
[AM tutorial](https://github.com/OpenXiangShan/XiangShan-doc/blob/main/tutorial/others/%E4%BD%BF%E7%94%A8%20AM%20%E7%94%9F%E6%88%90%E8%87%AA%E5%AE%9A%E4%B9%89%20workload.md)


### Checkpoints (Generic RISC-V Checkpoints)

### SPECCPU 2006

### Real applications!

WIP...
