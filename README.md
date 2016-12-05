Computer Systems Organization - Recitation 13: 
Dynamic Memory Allocation
==========

Exercise -- Block Sizes and Headers
-----

Determine the block size and header values that would result from the following sequence of malloc requests. Assumptions:

* The allocator maintains double-word alignment (8 bytes)
* The allocator uses an implicit free list
* Block sizes are rounded up to the nearest multiple of 8 bytes

|     Request      | Block Size (decimal bytes)| Block Header (hex)    |
| :--------------: | :-----------------------: | :-------------------: |
| malloc(1)        |                           |                       |
| malloc(5)        |                           |                       |
| malloc(12)       |                           |                       |
| malloc(13)       |                           |                       |

Exercise -- Minimum Block Size
-----

Determine the minimum block size for each of the following combinations of alignment requirements and block formats. Assumptions:

* We are using an implicit free list
* Zero-size payloads are not allowed
* Headers and footers are stored in 4-byte words.

|     Alignment    |   Allocated Block        |    Free Block         | Minimum block size (bytes) |
| :--------------: | :----------------------: | :-------------------: | :--------------: |
| Single word      | Header and footer        | Header and footer     |                  |
| Single word      | Header, but no footer    | Header and footer     |                  |
| Double word      | Header and footer        | Header and footer     |                  |
| Double word      | Header, but no footer    | Header and footer     |                  |

Complete the last column of the table.

Exercise -- Implicit Free List Allocation
-----

The following problem concerns dynamic storage allocation.

Consider an allocator that uses an implicit free list. The layout of each allocated and free memory block is as follows:

```
           31                            2 1 0
           __________________________________
Header    |    Block Size (bytes)      |     |
          |____________________________|_____|
	      |                                  |
	      |                                  |
	      |                                  |
	      |__________________________________|
Footer    |    Block Size (bytes)      |     |
          |____________________________|_____|


```

Each memory block, either allocated or free, has a size that is a multiple of eight bytes. Thus, only the 29 higher order bits in the header and footer are needed to record block size, which includes the header and footer. The usage of the remaining 3 lower order bits is as follows:

* bit 0 indicates the use of the current block: 1 for allocated, 0 for free.
* bit 1 indicates the use of the previous adjacent block: 1 for allocated, 0 for free.
* bit 2 is unused and is always set to be 0.

Given the contents of the heap shown in the file `Heap.png`, show the new contents of the heap (in the right table) after a call to free(0x400b000) is executed.  Your answers should be given as hex values. Note that the address grows from bottom up. Assume that the allocator uses immediate coalescing, that is, adjacent free blocks are merged immediately each time a block is freed. If the content of a word did not change, you may leave it blank.


