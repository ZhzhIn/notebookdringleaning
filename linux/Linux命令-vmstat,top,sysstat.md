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
 