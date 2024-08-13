# micro-arch-training
How to make undergraduates or new graduates ready for advanced computer architecture research or modern CPU design.
本项目的目的是让本科生或新入学的研究生迅速地可以参加体系结构研究或参与高性能处理器开发。

# Off-topic

尽管我们主要在讨论计算机体系结构，但是我们强烈推荐大家扎实地学习好其他基础课程，例如计算机系统基础、操作系统、编译原理。
这些课程对理解微体系结构设计、帮助完成体系结构相关实验有非常大的帮助。
例如CPU中的寄存器重命名和编译器的寄存器分配其实互为“逆过程”，编译原理可以为你学习乱序执行提供一种全新的视角。
再例如，操作系统的中断返回和启动相关代码也可以用来制作体系结构研究用的Checkpoint。

## Introduction to Computer System

这部分的课程学习建议读CSAPP那本书，实验推荐做[NEMU Programming Assignment](https://nju-projectn.github.io/ics-pa-gitbook/ics2024/)。
这个实验让写一个可以启动简单操作系统、运行仙剑奇侠传的模拟器。

## Operating System

很幸运，我们找到了质量比较高的录制好的中文操作系统课程[南京大学 “操作系统：设计与实现” (蒋炎岩)](https://www.bilibili.com/video/BV1HN41197Ko)。
课程实验，我们推荐做[MIT 6.828的实验](https://pdos.csail.mit.edu/6.828/2021/xv6.html)，这个实验让写一个Non-trivial的操作系统。

## Compiler

我们暂时没有找到合适的中文公开课，所以推荐[Stanford CS 143](https://www.youtube.com/watch?v=SNWHmnWzJAI&list=PLoCMsyE1cvdUZRe1udlyjpzTww1U5olL2)
我们也推荐做[CS 143的实验课Cool Compiler](https://github.com/search?q=cool+compiler+lab)，因为实验材料需要从内网下载，所以我们只好在Github搜一个来做。
这个实验让写一个语法较为Fancy的编译器，然后生成汇编代码，可选做一些优化。

#### 实验素材

- [cpu0](https://jonathan2251.github.io/lbd/llvmstructure.html)

  推荐理由

  - 相比于其他compiler公开课的project，该项目只需实现后端，更“实用“（尽可能只关注优化 pass）
  - 基于riscv（不过emulator/os/compiler几乎都从X86迁移到riscv了）
  - 基于llvm实现，更现代一点

最后，因为如果有高质量的中文公开课或者更好的实验素材，欢迎大家可以发PR给我们推荐一下。我们希望以上的每门课都有一门高质量的中文公开课+一门高质量的英文公开课+高质量的实验课。

# Computer Architecture

现在我们回到正题——计算机体系结构。根据我们的了解，目前很多（高级）体系结构课都不够深入，无法保证学生在完成课程之后就能进行相关研究。
本项目希望弥补这一空缺，培养面向体系结构研究或者高性能处理器开发的能力，包括理论知识和实践能力。

理论知识部分，可以学习视频公开课，例如[Onur Mutlu的体系结构课](https://www.bilibili.com/video/BV1PT4y1M7gM?p=1)
或[David Wentzlaff的体系结构课](https://www.bilibili.com/video/av93575643)。
也可以参考公开的课程slides，例如[UWisc的ECE752](https://ece752.ece.wisc.edu/)或者
[UWisc的CS752](https://pages.cs.wisc.edu/~sinclair/courses/cs752/fall2020/includes/schedule.html)。
我个人比较喜欢[UWisc的ECE752](https://ece752.ece.wisc.edu/)，
因为 ECE752 在讲分支预测、寄存器数据流和访存数据流的时候，提供了非常多的参考文献，
可以说 Lecture 7-9 是 CPU 架构设计中经典算法的综述。

同时我们还看到有[Onur Mutlu的高级体系结构课](https://www.bilibili.com/video/BV1Vf4y1i7YG)这样的面向研究生的体系结构课程。
这类课程非常有深度，但是有时候和授课老师的研究方向强相关，比如Mutlu现在主要做Memory，所以这门课主要在讲Memory；
而ECE752的后续课程[ECE757](https://ece757.ece.wisc.edu/)主要讲多核架构和并行编程。

## Ads

我在2021年第一次写了这个小指南，可惜一直没有彻底完善。

现在我在招人，我发现时至今日（2023年），仍然很难招到扎实学习了上述4门课程的人（即完成理论课+课程实验）。
如果你在求职，并且扎实学习过其中2-3门，欢迎给我发简历：archshinez at outlook dot com

## Slides

WIP...

## Papers

++ 标注的是初学者应该先学习的论文

### 乱序执行

++ [MIPS R10000](https://pages.cs.wisc.edu/~markhill/restricted/ieeemicro96_r10000.pdf)

[An Efficient Algorithm for Exploiting Multiple Arithmetic Units](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5392028)

[HPS, a new microarchitecture: rationale and introduction](http://ezproxy.lib.utexas.edu/login?url=http://doi.acm.org/10.1145/18927.18916)

[Critical issues regarding HPS, a high performance microarchitecture](http://ezproxy.lib.utexas.edu/login?url=http://doi.acm.org/10.1145/18927.18917)

++ [Complexity-Effective Superscalar Processors](http://ftp.cs.wisc.edu/sohi/papers/1997/isca.complexity.pdf)


### 数据流架构

[The Manchester Prototype Dataflow Computer](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.587.5154&rep=rep1&type=pdf)

[Executing a program on the MIT tagged-token dataflow architecture](https://ieeexplore.ieee.org/document/48862/)

[Scaling to the End of Silicon with EDGE Architectures](http://www.cs.utexas.edu/users/cart/trips/publications/computer04.pdf)


### 性能测量与分析

++ [SimPoint ASPLOS-2002](https://cseweb.ucsd.edu/~calder/papers/ASPLOS-02-SimPoint.pdf)

[SMARTS](https://infoscience.epfl.ch/record/135578/files/isca03_smarts.pdf)

++ [A performance counter architecture for computing accurate CPI components](https://dl.acm.org/doi/abs/10.1145/1168918.1168880)

[A top-down method for performance analysis and counters architecture](https://ieeexplore.ieee.org/abstract/document/6844459/)


### 流水线前端设计

[A Scalable Front-End Architecture for Fast Instruction Delivery](https://dl.acm.org/doi/pdf/10.1145/307338.300999)

[Fetch directed instruction prefetching](https://ieeexplore.ieee.org/abstract/document/809439)

[Re-establishing Fetch-Directed Instruction Prefetching: An Industry Perspective](https://ieeexplore.ieee.org/abstract/document/9408197)


### 分支预测

[A Study of Branch Prediction Strategies](http://portal.acm.org/citation.cfm?id=801871)

[Two-Level Adaptive Training Branch Prediction](https://dl.acm.org/citation.cfm?id=123475)

[The Agree Predictor: A Mechanism For Reducing Negative Branch History Interference](http://ezproxy.lib.utexas.edu/login?url=http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=604711)

[Dynamic Branch Prediction with Perceptrons.](http://www.cs.utexas.edu/~lin/papers/hpca01.pdf)

++ [Analysis of branch prediction via data compression](https://dl.acm.org/citation.cfm?id=237171)

[Analysis of the OGEHL predictor](http://www.irisa.fr/caps/people/seznec/ISCA05.pdf)

[TAGE](https://hal.inria.fr/hal-03408381/document)


### 数据预取

[Effective hardware-based data prefetching for high-performance processors](https://ieeexplore.ieee.org/abstract/document/381947)

++ [SMS](https://dl.acm.org/doi/abs/10.1145/1150019.1136508)

[Best-offset hardware prefetching](https://ieeexplore.ieee.org/abstract/document/7446087)

[Temporal prefetching without the off-chip metadata](https://dl.acm.org/doi/abs/10.1145/3352460.3358300)



### 缓存替换

[A Case for MLP-Aware Cache Replacement](https://dl.acm.org/citation.cfm?id=1136501)

++ [High performance cache replacement using re-reference interval prediction (RRIP)](https://dl.acm.org/doi/abs/10.1145/1816038.1815971)

[SHiP: signature-based hit predictor for high performance caching](https://dl.acm.org/doi/abs/10.1145/2155620.2155671)


### Consistency Models

[How to Make a Multiprocessor Computer That Correctly Executes Multiprocess Programs](http://research.microsoft.com/users/lamport/pubs/multi.pdf)

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

NUMA 的问题讨论很多了，看wiki吧。

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
- 原则上，所有服务器都应该禁止用密码登录

### Version control

版本控制的基本要求是学习以下命令的使用：

```
git add -p
git commit
git commit --amend
git checkout an-existing-branch
git checkout -b a-new-branch
git checkout path/to/a/file

git format-patch
git apply
git apply --check
git am

git rebase -i

git rm
git rm --cached

git fetch

git push

git merge a-branch
```

如果要参与复杂的开源项目开发，你或许还需要掌握这些命令：

```
git reset -p
git add -p
git checkout -p

git rebase a-branch
git rebase a-commit
git rebase --onto new-base-commit old-base-commit newest-modified-commit
git cherry-pick

git commit --fixup
```
可以参考[一位同学写的GIT学习笔记](https://zhuanlan.zhihu.com/p/526826127)

记住：
- 不要用`git add .`，最好用`git add -p`
- 99%的情况，不要track log文件
- 99%的情况，不要track binary文件

## Simulator - GEM5

这里是上手用GEM5的入门训练

### Build GEM5

这部分请看官方文档，就不展开了。

### Configure GEM5

题目：
配置GEM5的Cache如下：
`16 kB L1 I-Cache + 16 kB L1 D-Cache + 256kB L2 Cache + 2M L3 Cache; L2 and L3 Mostly exclusive; L1 and L2 Writeback clean`，
并对比Mostly-exclusive配置下，Writeback clean开与关的性能差别。
关于workload，SPECCPU里的bzip2和bwaves都适合作为测试用例。
或许读者不知道什么是`Mostly exclusive`和`Writeback clean`，需要主动去搜索学习或者阅读代码。
<!-- 把[这里编译好的Coremark](#coremark)作为payload，运行GEM5，采集数据。 -->


### Compile a broken GEM5

目的：学习C++的模板和SFINAE

题目：尝试使这个无法构建的GEM5项目通过编译和链接：[gem5-quiz](https://github.com/OpenXiangShan/GEM5/tree/gem5-test-1)
- 需要额外安装boost库，因为我们这个用到了boost
- 构建过程最终会在链接的时候报错，需要找到出错原因并修复


### GEM5 statistics

学习GEM5的数据统计方法。了解 statistics::Scalar, statistics::Vector, statistics::Formula, statistics::Distribution的用法，
具体可以用grep读一读代码。 然后增加一些性能计数器，

题目：
用statistics::Vector统计每个周期发射（issue）的load指令的条数分布，例如
```
0条：500周期
1条：111周期
2条：50周期
...
```
最后，再用statistics::Distribution统计每个周期发射（issue）的load指令的条数分布。

### Event-driven programming

子题目1: 在GEM5退出时，Dump cache中所有的line的地址和内容，
参考[Event-driven programming](https://www.gem5.org/documentation/learning_gem5/part2/events/)，
但是退出的event callback和这里展示的例子不完全一样，需要自己去阅读相关代码。

子题目2：在退出时Dump cache中所有的line的地址和内容，按照Least Important的顺序导出。例如，当使用LRU替换算法时，用LRU序导出；
当使用RRIP算法是，先导出RRI较大的，后导出RRI较小的。
希望可以找到一种不需要触及替换算法本身的dump方法。

### Add new configurable parameter 

参考资料：[学习GEM5如何增加参数](https://www.gem5.org/documentation/learning_gem5/part2/parameters/)

题目：给se.py或者fs.py 增加一个参数--dump-cache，当带上这个参数的时候，退出时按照Event-driven programming中的要求dump cache；否则不进行dump。

### GEM5 debug flags

目的：学习GEM5的printf调试系统，以及加强对参数系统的理解。

参考资料：[Debugging gem5](https://www.gem5.org/documentation/learning_gem5/part2/debugging/)

题目1：给GEM5增加一个debug flag：`CacheMiss`，当发生cache miss的时候，打印出cache miss的地址。

题目2：给GEM5增加一个参数：`--observe-cache-miss`，他的可选值为：['L1d', 'L1i', 'L2', 'L3']，
当带上这个参数的时候且开启了`CacheMiss` debug flag ，在发生cache miss时打印出`--observe-cache-miss`所指定的那一块cache发生miss的地址。
（注意，题目1是打印所有，题目2是只打印选定的cache）
针对题目2，至少需要阅读：`src/mem/cache/Cache.py`，`configs/common/Caches.py`。

### Out-of-order core

这部分的目的是，学习GEM5如何实现乱序执行。

题目1：
统计指令之间的寄存器依赖：统计有依赖的两条指令之间的“距离”分布，“距离”是指两条指令的seqNum之差。
其中，“有依赖”是指两条指令之间有寄存器依赖，“依赖距离”是指两个有依赖的指令的seqNum。
这些指令不一定是最终提交的指令，在分支预测错误的路径上也没关系。
将分布统计为如下形式：
```
distance < 10: xxx
10 <= distance < 20: xxx
20 <= distance < 40: xxx
40 <= distance < 80: xxx
distance > 80: xxx
```
提示：阅读O3 CPU的`InstQueue`和`dependGraph`这两个类，并修改其中的数据结构和函数进行统计。

### Batch running

Tool Task:
利用[BatchTaskTemplate](https://github.com/shinezyy/DirtyStuff.git)批量运行GEM5。
具体地，拷贝一份`gem5tasks/restore_gcpt.py`，仔细阅读注释，修改里面的配置，把GEM5批量跑起来。

### Collecting statistics

### Collecting batch-running statistics

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
