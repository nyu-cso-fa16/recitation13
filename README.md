Computer Systems Organization: Recitation 13
==========

Exercise -- Cache Organization
-----

Complete the problems in `Cache Organization.pdf`

Exercise -- Dynamic Memory Allocation
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