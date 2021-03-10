1.vmstat
    -金宠procs
        - r等待运行
        - b 非终端睡眠状态邪恶
        - w被交换出去的可运行的
    - 内存（memory）
        - sqpd 虚拟内存使用请款给，单位kb
        - free 空闲的内存
        - buff 被用来做缓存的内存
        -cache 被用来做数据缓冲区的内存
    - 交换分区 sqap
        - si 从磁盘交换到内存的交换也苏良，kb/s
        - so 从内存交换到磁盘的交换也数量
    - 输入输出 IO
        - bi 发送到快设备的快书
        - bo 从块设备接收到的块数
    - 系统 system
        - in 每秒的终端数，包括时钟中断
        - cd 每秒的环境切换次数
    - cpu 按cpu总是用时间的百分比来显示
        - us cpu用户使用时间
        - sy cou 系统使用时间
        - id cpu限制时间
 |类别 |计数器名称 |描述 |
 |memory |free |可用物理内存书 |
 |memory |swap |已使用的虚拟内存数量 |
 |memory |(page)si |每秒从磁盘交换到内存的数量 |
 |memory |(page)so |每秒从内存交换出的内存数量 |
 |memory |cache |文件系统缓存 |
 |process进程 |%CPU Usage |进程小号的处理器时间 |
 |process进程 |Page fault count |该进程产生的页面失败次数 |
 |process进程 |Resident size |进程保留的使用内存量，该数值等于进程的代码使用内存+进程的数据使用内存 |
 |process处理器 |%Idle Time |cpu总的空闲时间。如果改制持续低于10%，表明平静时CPU |
 |process处理器 |%User time |非内核操作耗费的cou时间 |
 |process处理器 |%Kernel time |cou内核时间时在核心模式下处理线程执行代码所花时间的百分比 |
 |process处理器 |IOWait time |Cpu 小号在等待io处理上的时间，辞职需要结合io的数据考虑  |
 |physical disk  |average num of transactions activity |值读取和吸入请求的平均数（为所选侧畔在是李剑阁中离队的） |
 |physical disk  |percent of time the disk is busy|值所选磁盘驱动器忙于唯独或写入请求提供服务所用的时间的百分比 |
 |physical disk  |being services average num of transactions waiting 4 service |治读取（写入）请求队列的平均数 |
 |physical disk  |Reads (Writes)per sec|物理磁盘上每秒磁盘读写次数，两者相加，营销与磁盘设备的最大容量。在iostat的结果中，改制显示为r/s 和w/s |
 |physical disk  |average services average num of transactions waiting 4 service |值以毫秒计算的在磁盘上读取和写入数据的所需平均时间，在iostat的结果中，改制显示为asvc t |
 |physical disk  |the num of disk operations per sec |显示每个磁盘每秒的被操作次数 |
 | system  |%User Time |系统上所有处理器执行肺内和操作的平均时间百分比 |
 | system  |CPU context swwitches |处理器上下文切换次数 |
 
2.数据解析
CPU：
1.进程处理时间=%User Time +%privileged Time ,实际上就是指程序分别处于操作系统的User模式和Kernel模式的时间。操作系统的IO和系统服务一般运行在kernel模式，程序一般在User模式下运行，但对系统的调用处于kernel模式下
大部分情况下%privileged time <<%User Time ，因此，%User Time 在很大程度上代表了%Processor Time.
2.Context Switches/sec （系统对象的每秒上下文切换）不要大于10k~20k。
长时间CPU服务一个程序，其他程序会等待导致服务质量下降，CPU采用时间片来分别给服务不同的程序。
3.系统对向下的处理器队列长度 Processor Queue Length < CPU核数+1.
操作系统会维护一个等待CPU处理的线程队列，如果在这个队列中，数目超过前面所说的值，会出现阻塞，CPU性能下降。一般%Processer Time 很高时都有可能伴随阻塞。

3.磁盘相关的数据指标
    1.LogicalDisk -%Free Space ，表示当前没有使用的磁盘占比，<15则说明磁盘空间不足
    2.PhisicalDisk-%Idle Time ，表示当前观察时间间隔内，磁盘空间的时间。<20则说明磁盘工作状态比较重，需要考虑替换读写速度更快的磁盘
    3.PhisicalDisk-avg disk sec/Read 平均读取时间，代表每次从磁盘读取数据所花费的时间，如果>25ms，则说明磁盘读取有所延迟，对于一些关键应用，<10ms
    4.PhisicalDisk-avg disk sec/Write 平均写入时间，代表每次写入花费时间。同上<25ms
    5.PhysicalDisk -avg.Disk Byte/transfer,代表读写操作从磁盘上传输字节的平均数。因为读的频率>>写，所以也可以用avg.Disk byte/Read代替
    如果AvgDisk byte/transfer数值较小，但%Idle Time 数值却很低，Average Disk Queue Length 的值又很高，则很大程序上说明磁盘性能存在瓶颈：磁盘空闲时间很少，忙于处理读写，但等待队列有多。
    如果average disk queue length 很高，avg.disk byte/transfer也比较高，则不能说明磁盘的问题，很可能是内存不足造成的数据排队等待进入磁盘现象。
    IO与mem,cpuyingxiang henda .如果mem的cache byte（缓存字节）很大，>200mb，则表明磁盘存在瓶颈。
    