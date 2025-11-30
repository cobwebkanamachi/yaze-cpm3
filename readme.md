Hey this repos is re-experiment for great work of https://github.com/cobwebkanamachi/yaze-cpm3 .

reproducible procedure
1. get https://github.com/begoon/yaze
   git clone https://github.com/begoon/yaze
2. change Makefile
   [cobweb@yaze]$diff Makefile.org Makefile
   27c27,28
   < OPTIONS             = -DBIOS -D_BSD_SOURCE
   ---
   > #OPTIONS            = -DBIOS -D_BSD_SOURCE
   > OPTIONS             = -D_BSD_SOURCE -DMEMSIZE=128 -DMMU
   30c31
   < YAZE_OBJS     = yaze.o simz80.o bios.o monitor.o
   ---
   > #YAZE_OBJS     = yaze.o simz80.o bios.o monitor.o
   32c33
   < #YAZE_OBJS    = yaze.o simz80.o io.o
   ---
   > YAZE_OBJS    = yaze.o simz80.o io.o
3. make
4. https://www.moria.de/~michael/cpmtools/
   I have installed them, so passed this.
5. get https://www.moria.de/~michael/yaze-cpm3/yaze-cpm3.zip
   unzip
6. edit do.sh (new) edit content bellow two lines
   mkfs.cpm -b bootload.com -b cpmldr.com cpm-3
   cpmcp cpm-3 cpm3.sys ccp.com halt.com 0:
7. bash do.sh
   after execution, you have cpm-3 file (diskimage)
8. edit start (new)
   mount a cpm-3
   attach rdr /dev/null
   attach lst lst
   attach pun /dev/null
9. cd yaze-cpm3
   ./yaze -l 0 -b ./diskboot.rom -s start
   then splash!
   CP/M V3.0 Loader
   Copyright (C) 1998, Caldera Inc.

   61K TPA


   CP/M Version 3.0
   BIOS Copyright (C) 1989 by Udo Munk

   A>quit
   QUIT?
   A>HALT
   HALT
   PC   SP   IR   IX   IY   AF   BC   DE   HL   AF'  BC'  DE'  HL'
   0105 f4fe 0000 0000 0000 0144 0031 f492 0000 0000 0000 0000 0000
   F0   F1   F2   F3   F4   F5   F6   F7   F8   F9   Fa   Fb   Fc   Fd   Fe   Ff
   0010 0011 0012 0013 0014 0015 0016 0017 0018 0019 001a 001b 001c 001d 001e 000f

That is all!.
Enjoy!
