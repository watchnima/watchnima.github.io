## rev.ng项目文献调研

[TOC]

#### CASES 2016 《A jump-target identification method for multi-architecture static binary translation》

##### 基本信息

**静态翻译的步骤**

* 解析一个输入二进制文件
* 找出它包含的所有代码
  * 二进制文件分块
  * 标记可执行块
  * 所有代码包含在可执行块中
* 从输入架构翻译成目标架构
* 生成一个输出二进制文件

**基本块**：一个跳转目标确定一个基本块（基本快介于两个跳转目标之间）

一种找出基本块的方案：1.从入口开始探索代码 2.跟着控制流走 3.彻底搜集所有控制流图

**问题**

1. 面临复杂的间接流控制转换，分为四类：
   1. 返回指令
   2. 调用函数指针 
   3. 长跳转（将新地址存在寄存器中）
   4. switch语句
2. 同一语句不同架构的二进制代码流不同

**解决方案**

1. 使用**QEMU**作为前端，支持17种架构，生成中间代码tiny code；

2. 使用**LLVM**编译上述翻译好的代码。

**基本块确认流程**

1. 全局数据捕获
2. 简单表达式追踪（SET）
3. 偏移移位范围分析（OSRA，解决switch语句）



#### CC 2017 《A Unified Binary Analysis Framework to Recover CFGs and Function Boundaries 》

##### 基本信息

**二进制分析的挑战**

* 控制流图恢复
  * 
* 函数边界恢复