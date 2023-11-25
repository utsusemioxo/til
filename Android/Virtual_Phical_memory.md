# Virtual memory and Physical memory on android

## Virtual Memory

虚拟内存：当每个进程创建的时候，内核会为进程分配很大空间的虚拟内存，顾名思义，虚拟的、事实上不存在，在一个进程的虚拟内存空间里，只存在进程自己和系统内核。当对虚拟内存进行写操作的时候，系统就会逐步分配物理内存，并把虚拟内存映射到物理内存上。

## Physical Memory

物理内存：即移动设备上的RAM（8G，16G），当启动一个Android程序的时候，会启动一个Dalvik VM进程，系统会给它分配固定的内存弓箭（16M，32M不定），这块内存空间会映射到RAM上某个区域，然后这个Android程序就会运行在这块空间上。