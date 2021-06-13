# notekook
## Introduction
recode some tips in learning
## Code Language
### Rust
* What's the good points of Rust 
    * Memory security
    * Error handle
    * Without gc
    * Cross platform
    * Performance
    * Multithreading
    * Life time
#### Important Data Structure
* Personal rust project
### Golang
* What's the good points of Golang
    * 轻量级线程 
* Short point
    * Copy Default
        * Do not copy Mutex
* What's the good points of Golang 
* Important Data Structure
* Concurrent
    * hashMa and sync.Map is unscalable
    * 大多数场景读操作远多于写操作
        * 数据分区域给CPU抢占 
    * skipmap
* Scheduler
    * 调度循环
    * 协作与抢占
        * GPM
            * G Goroutine:代表一个执行流，本身有栈，寄存器PC,SP，当与MP结合之后就把PC和SP给CPU，即可得到执行
            * M Machine:线程，拥有本地私有变量，每个M内部都有一个g0
            * P Processor(逻辑):提供G执行的资源
        * 协作式调度：依靠被调度方主动放弃
            * 用户主动让权：runtime.Gosched调用主动让出执行机会；
            * 主动调度弃权
        * 抢占式：依靠调度器强制将被调度方中断
            * 被动监控抢占： G执行时间太长
            * 垃圾回收，强迫停止所有的G
* GC && Memory management
* Personal project
#### Important Data Structure
* Mutex
    * Non-Reentrant mutex
* sync.map
* atomic.Value
    * store read only data
* race detector
    * detector problem
* Develop of Mutex
    * Lock Memory bus
    * MESI protocol
        * Invalid,Exclusive,Shared,Modified
    * Spin Lock
        * use in wait time short
    * Mutex
        * 正常模式: FIFO 的顺序排队获取锁,新到的goroutine先获取锁，等待时间超1ms->饥饿模式
        * 严格排队，适时->正常模式
        * 效率：正常模式更高
            * 减少调度
            * 利用缓存

#### Test
 * race detector
    * 10 times cpu consumption

## Computer System
### System call
### Synchronous between multiple thread
* Optimize of Lock
    * reduce holding time
    * optimize lock's granularity
        * Shrink the critical section
        * Separate data, such as use sub map in a big map
    * read/write separate
        * RWMutex
        
    * use atomic types
        * lock free, no trigger schedule

## Design Pattern
### Structural
* Bridge
* Facade
### Behavioral
* Observer && Visitor 

## Block chain
### Consensus
* POW
* PBFT
* POS
* DPOS
### Contract
* Wasm
* Parity
* Ink

### Virtual Machine
* EVM
* WASM

### Transaction
* What is double spending and how to avoid
* 

### Storage

### Network
#### DNS
#### Socket

### Cryptography
* Zero-knowledge proof 
