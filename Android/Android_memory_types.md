# Android memory types

Android 内存分配相关知识总结 [<sup>1</sup>](#refer-anchor-1)

![Alt text](memory-types.svg)

## Types of memory

- RAM is the fastest type of memory, but is usually limited in size. High-end devices typically have the largest amount of RAM.

- zRAM is a partition of RAM used for swap space. Everything is compressed when placed into zRAM, and then decompressed when copied out of zRAM. This portion of RAM grows or shrinks in size as pages are moved into or taken out of zRAM. Device manufactures can set the maximum size.

- Storge contains all of the persistent data such as the file system and the included object code for all apps, libraries, and the platform. Storage has much more capacity than the other two types of memory. On Android, storage isn't used for swap space like it is on other Linux implementations since frequent writing can cause wear on this memory, and shorten the life of the storage medium.

## Memory Pages

RAM is broken up into *pages*. Typically each page is 4KB of memory.

Pages are considered either *free* or *used*. Used pages are RAM that the system is actively using, and are grounped into the following categories:

- Cached: Memory backed by a file on storage (for example, code or memory-mapped files).
  - Private: Owned by on process and not shared
    - Clean: Unmodified copy of a file on storage, can be deleted by `kswapd` to increase free memory
    - Dirty: Modified copy of the file on storage, can be moved to, or compressed in, zRam by `kswapd` to increase free memory
  - Shared: Used by mutiple processes
    - Clean: Unmodified copy of the file on storage, can be deleted by `kswapd` to increase free memory
    - Dirty: Modified copy of the file on storage; allows changes to be written back to the file in storage to increase free memory by `kswapd`, or explicitly usimg `msync()` or `munmap()`



- Annoymus: Memory not backed by a file on storage (for example, allocated bt mmap with the `MAP_ANONYMOUS` flag set)
  - Dirty: Can be moved/compressed in zRAM by `kswapd` to increase free memory

> Why these concepts importent? They are key to managing low-memory situations.

-----
## references
<div id="refer-anchor-1"></div>

- [1] [Memory allocation among processes](https://developer.android.com/topic/performance/memory-management)