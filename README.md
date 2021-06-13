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
    * 自动GC
* Notice
    * 函数参数都是值传递
* Short point
    * Copy Default
        * Do not copy Mutex
* What's the good points of Golang 
* Important Data Structure
    * array: 
        * 需指明长度，长度不可变
        * 长度为其类型中e 组成部分
        * 在作为函数参数时会产生copy
    * slice
        * growslice
            * cap < 1024,*2
            * cap >= 1024,*1.25
        * 预先分配内存可以提高性能
        * 直接使用index赋值比append性能要好
        * 没有发生扩容，修改在原来的内存中
        * 发生了扩容，修改会在新的内存中
        * nil slice
            * []Type{}或者make([]Type)初始化后，slice不为nil
            * var x []Type后，slice为nil
        * Bounds Checking Elimination
            * 能确定需要访问的长度可以执行一次让编译器做优化
    * map
        * 是值的指针，传参时传指针
        * map扩容，地址或改变
        * map存值，会发生copy
        * 删除key不会缩容
    * channel
        * 有锁
        * 底层有ringbuffer
        * 会触发调度
        * 高并发高性能不适合channel
        * un/buffer channel
            * buffer channel会发生两次copy
                * send goroutine -> buf
                * buf -> receive goroutine
            * unbuffered channel一次copy
                * send goroutine -> receive goroutine
            * unbuffered channel receive完成后send才会返回
        * select closed channel
            * for+select closed channel会造成死循环
            * select 中break无法跳出for循环
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
    * GC:a form of automatic memory management
        * reference counting
        * Tracing
            * GC Root
            * GC Heap
        * Style
            * Copying GC
            * Mark Sweep GC
    * memory allocator
        * Sized
            * Tiny
            * Small
            * Huge
        * when
            * GOGC threadhold
            * runtime.GC
            * runtime.forcegperiod(120s)
    * monitor tools
        * pprof
        * GClog
    * memory problem
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
