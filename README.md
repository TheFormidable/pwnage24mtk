```bash
vboxuser@UBUNTU:~/Desktop/pwnage24mtk-main$ python parse-part-img.py lk.img --split -o out
[DEBUG] Start Split Images --- lk.img
out/lk.bin: offset=0x0 size=1005824 image=lk load_addr=4294967295 (0xffffffff) [fake addr]
out/bl2_ext.bin: offset=0xf5900 size=961808 image=bl2_ext load_addr=4294967295 (0xffffffff) [fake addr]
out/aee.bin: offset=0x1e0610 size=964208 image=aee load_addr=4294967295 (0xffffffff) [fake addr]
out/lk_main_dtb.bin: offset=0x2cbc80 size=400000 image=lk_main_dtb load_addr=4294967295 (0xffffffff) [fake addr]
out/lk_dtbo.bin: offset=0x32d700 size=88976 image=lk_dtbo load_addr=4294967295 (0xffffffff) [fake addr]
wrote 5 sub-image(s) to out
vboxuser@UBUNTU:~/Desktop/pwnage24mtk-main$ python parse_preloader.py preloader_duchamp.bin
Loading image: preloader_duchamp.bin
File size     : 0xBB93C (768316 bytes)

============================================================
  MTK Preloader Image Analysis
============================================================

Image Type        : DIRECT
Header Offset     : 0x0

------------------------------------------------------------
  Preloader Header Fields
------------------------------------------------------------
Load Address      : 0x02000F10  (offset 0x1C - 0x20)
Preloader Size    : 0xBB93C (768316 bytes)  (offset 0x20 - 0x24)
Header Size       : 0xF0 (240 bytes)  (offset 0x28 - 0x2C)
IDA Offset        : 0x000000F0  (offset 0x30 - 0x34)

------------------------------------------------------------
  Computed Values
------------------------------------------------------------
Data Block Size   : 0xBB84C (768076 bytes)  [Preloader Size - Header Size]
IDA Load Address  : 0x02001000  [Preloader Load Address + IDA Offset]
                  :  (0x02000F10 + 0x000000F0)

------------------------------------------------------------
  Block Offsets in Image
------------------------------------------------------------
Header File Offset: 0x0
Data Block File Offset: 0xF0

============================================================
Preloader Load Addr  : 0x02000F10  (from header)
Data Block Load Addr : 0x02001000  (IDA Load Address)

Architecture    : ARM64 (64-bit)

------------------------------------------------------------
  Policy Part Map Analysis
------------------------------------------------------------

Address Space     : All pointers in data block use IDA Load Address 0x02001000 as base

'default\0' String Analysis:
  File Offset      : 0x8D2E5
  Data Offset      : 0x8D1F5
  Memory Address   : 0x0208E1F5 (data_block_load_addr + 0x8D1F5)

'default_mem_addr' Found in Image:
  File Offset      : 0xA8198
  Searched Bytes   : f5e1080200000000

Policy Part Map:
  File Offset      : 0xA8190
  Entry Size       : 0x38 bytes (56 bytes)

------------------------------------------------------------
  Policy Part Map Entries
------------------------------------------------------------

  #    | SW ID      | part_name1               | part_name2               | part_name3               | part_name4               | sec_sbcdis_lock  | sec_sbcdis_unlock  | sec_sbcen_lock  | sec_sbcen_unlock 
  --- -|----       -|----                     -|----                     -|---                     -|----                     -|----             -|----               -|---            -|----              
  0    | 0          | default                  | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  1    | 0          | preloader                | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  2    | 0          | lk                       | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  3    | 0          | logo                     | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  4    | 0          | boot                     | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  5    | 0          | system                   | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  6    | 0          | tee1                     | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  7    | 0          | tee2                     | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 2                
  8    | 0          | oemkeystore              | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  9    | 0          | keystore                 | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  10   | 0          | userdata                 | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  11   | 0          | modem                    | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  12   | 0          | md1dsp                   | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  13   | 0          | md1arm7                  | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  14   | 0          | md3img                   | (null)                   | (null)                   | (null)                   | 1                | 0                  | 3               | 0                
  15   | 0          |                          | (null)                   | (null)                   | (null)                   | 0                | 0                  | 0               | 0                
  16   | 0          |                          | (null)                   | (null)                   | (null)                   | 0                | 0                  | 0               | 0                
------------------------------------------------------------
  Total entries: 17

------------------------------------------------------------
  res_mem_info (Memory Region Information)
------------------------------------------------------------

  Found via        : BL33-reserved string pointer search
  Array Offset     : 0x9FF38
  Entry Count      : 13

  #    | name                 | start            | size             | align            | mapping 
  --- -|----                 -|----             -|---             -|----             -|----     
  0    | mb_kernel            | 0x0000000040000000 | 0x0000000007C80000 | 0x0000000000001000 | 0x00000000
  1    | mb_dtb               | 0x0000000047C80000 | 0x0000000000400000 | 0x0000000000001000 | 0x00000000
  2    | aee_debug_kinfo      | 0x0000000048080000 | 0x0000000000010000 | 0x0000000000010000 | 0x00000000
  3    | pstore               | 0x0000000048090000 | 0x00000000000E0000 | 0x0000000000010000 | 0x00000000
  4    | minirdump            | 0x0000000048170000 | 0x0000000000010000 | 0x0000000000010000 | 0x00000000
  5    | BL31-reserved        | 0x0000000048800000 | 0x0000000000200000 | 0x0000000000001000 | 0x00000000
  6    | pl-drambuf           | 0x0000000048500000 | 0x0000000000100000 | 0x0000000000001000 | 0x00000001
  7    | pl-boottag           | 0x0000000048600000 | 0x0000000000100000 | 0x0000000000001000 | 0x00000001
  8    | aee_lk               | 0x000000007E000000 | 0x0000000000800000 | 0x0000000000001000 | 0x00000001
  9    | BL33-reserved        | 0x0000000050700000 | 0x0000000012000000 | 0x0000000000001000 | 0x00000000
  10   | system_bl2-ext       | 0x0000000078000000 | 0x0000000002000000 | 0x0000000000001000 | 0x00000000
  11   | mb_ramdisk           | 0x0000000066F00000 | 0x0000000004000000 | 0x0000000000001000 | 0x00000000
  12   | security_tee_sig     | 0x000000006FFFF000 | 0x0000000000001000 | 0x0000000000001000 | 0x00000000
  --- -|----                 -|----             -|---             -|----             -|----     
  Total entries: 13

------------------------------------------------------------
  Derived Load Addresses
------------------------------------------------------------

  BL2_EXT Load Address (from system_bl2-ext): 0xFFFF000078000000
  LK   Load Address (from BL33-reserved    ): 0xFFFF000050700000

============================================================
  Analysis Complete
============================================================
vboxuser@UBUNTU:~/Desktop/pwnage24mtk-main$ python sign_mtk_cert.py /home/vboxuser/Desktop/pwnage24mtk-main/out/bl2_ext.bin -w
Name: bl2_ext.bin  Size: 961808
Found CERT2 at offset 0x000ea730, blob_off=0x000ea930, dsz=982
Image Header Hash (orig): c4ec9ac1d1210ce6bc4a2ffdb5131e25640530141d977783fb5ba0f042a3a491
Detected header hash algorithm: sha256
Image Hash (orig): f10696058ecb16966daca2498aab2ffecb187c88b70a2b198f90d7779aabc372
Detected image hash algorithm: sha256
Image Header Hash (calc): c4ec9ac1d1210ce6bc4a2ffdb5131e25640530141d977783fb5ba0f042a3a491
Image Hash (calc): f10696058ecb16966daca2498aab2ffecb187c88b70a2b198f90d7779aabc372
CERT2 new dsize=1072, padded=1072, align=16
Write complete: /home/vboxuser/Desktop/pwnage24mtk-main/out/bl2_ext.bin.signed
vboxuser@UBUNTU:~/Desktop/pwnage24mtk-main$ python build-part-img.py replace lk.img --name bl2_ext --file /home/vboxuser/Desktop/pwnage24mtk-main/out/bl2_ext.bin.signed
wrote rebuilt image to lk.img.new
vboxuser@UBUNTU:~/Desktop/pwnage24mtk-main$ 
```
