The width of Family/Model/Stepping is 12/8/4bit, but when arranged in the
32bit processor signature raw data is like 0FFM0FMS, hexadecimal.
e.g. if a processor signature is 0x000906eb, it means
Family=0x006, Model=0x9e and Stepping=0xb

mine is 

````
iucode_tool: system has processor(s) with signature 0x000906ea
microcode bundle 1: (stdin)
selected microcodes:
  001/177: sig 0x000906e9, pf_mask 0x2a, 2019-04-01, rev 0x00b4, size 99328
  001/178: sig 0x000906ea, pf_mask 0x22, 2019-04-01, rev 0x00b4, size 98304
  001/179: sig 0x000906eb, pf_mask 0x02, 2019-04-01, rev 0x00b4, size 99328
  001/180: sig 0x000906ec, pf_mask 0x22, 2019-02-14, rev 0x00ae, size 98304
  001/181: sig 0x000906ed, pf_mask 0x22, 2019-03-17, rev 0x00b8, size 97280
````

then

if a processor signature is 0x000906eb, it means
Family=0x006, Model=0x9e and Stepping=0xb

to 0x000906ea

signature | family | model | stepping 
----|-----|-----|-----|-----
0x000906eb | 0x006 | 0x9e | 0xb 
0x000906ea | 0x006 | 0x9e | 0xa ? 

Processor             Identifier     Version       Products
Model        Stepping F-MO-S/PI      Old->New
---- updated platforms ------------------------------------
CFL-H/S/E3   U0       6-9e-a/22 000000aa->000000b4 Core Gen8 Desktop, Mobile, Xeon E


releasenote

Processor             Identifier     Version       Products
Model        Stepping F-MO-S/PI      Old->New
---- new platforms ----------------------------------------
VLV          C0       6-37-8/02           00000838 Atom Z series
VLV          C0       6-37-8/0C           00000838 Celeron N2xxx, Pentium N35xx
VLV          D0       6-37-9/0F           0000090c Atom E38xx
CHV          C0       6-4c-3/01           00000368 Atom X series
CHV          D0       6-4c-4/01           00000411 Atom X series
CLX-SP       B1       6-55-7/bf           05000021 Xeon Scalable Gen2

---- updated platforms ------------------------------------
SNB          D2/G1/Q0 6-2a-7/12 0000002e->0000002f Core Gen2
IVB          E1/L1    6-3a-9/12 00000020->00000021 Core Gen3
HSW          C0       6-3c-3/32 00000025->00000027 Core Gen4
BDW-U/Y      E0/F0    6-3d-4/c0 0000002b->0000002d Core Gen5
IVB-E/EP     C1/M1/S1 6-3e-4/ed 0000042d->0000042e Core Gen3 X Series; Xeon E5 v2
IVB-EX       D1       6-3e-7/ed 00000714->00000715 Xeon E7 v2
HSX-E/EP     Cx/M1    6-3f-2/6f 00000041->00000043 Core Gen4 X series; Xeon E5 v3
HSX-EX       E0       6-3f-4/80 00000013->00000014 Xeon E7 v3
HSW-U        C0/D0    6-45-1/72 00000024->00000025 Core Gen4
HSW-H        C0       6-46-1/32 0000001a->0000001b Core Gen4
BDW-H/E3     E0/G0    6-47-1/22 0000001e->00000020 Core Gen5
SKL-U/Y      D0/K1    6-4e-3/c0 000000c6->000000cc Core Gen6
BDX-ML       B0/M0/R0 6-4f-1/ef 0b00002e->0b000036 Xeon E5/E7 v4; Core i7-69xx/68xx
SKX-SP       H0/M0/U0 6-55-4/b7 0200005a->0000005e Xeon Scalable
SKX-D        M1       6-55-4/b7 0200005a->0000005e Xeon D-21xx
BDX-DE       V1       6-56-2/10 00000019->0000001a Xeon D-1520/40
BDX-DE       V2/3     6-56-3/10 07000016->07000017 Xeon D-1518/19/21/27/28/31/33/37/41/48, Pentium D1507/08/09/17/19
BDX-DE       Y0       6-56-4/10 0f000014->0f000015 Xeon D-1557/59/67/71/77/81/87
BDX-NS       A0       6-56-5/10 0e00000c->0e00000d Xeon D-1513N/23/33/43/53
APL          D0       6-5c-9/03 00000036->00000038 Pentium N/J4xxx, Celeron N/J3xxx, Atom x5/7-E39xx
APL          E0       6-5c-a/03 0000000c->00000016 Atom x5-E39xx
SKL-H/S      R0/N0    6-5e-3/36 000000c6->000000cc Core Gen6; Xeon E3 v5
DNV          B0       6-5f-1/01 00000024->0000002e Atom C Series
GLK          B0       6-7a-1/01 0000002c->0000002e Pentium Silver N/J5xxx, Celeron N/J4xxx
AML-Y22      H0       6-8e-9/10 0000009e->000000b4 Core Gen8 Mobile
KBL-U/Y      H0       6-8e-9/c0 0000009a->000000b4 Core Gen7 Mobile
CFL-U43e     D0       6-8e-a/c0 0000009e->000000b4 Core Gen8 Mobile
WHL-U        W0       6-8e-b/d0 000000a4->000000b8 Core Gen8 Mobile
WHL-U        V0       6-8e-d/94 000000b2->000000b8 Core Gen8 Mobile
KBL-G/H/S/E3 B0       6-9e-9/2a 0000009a->000000b4 Core Gen7; Xeon E3 v6
CFL-H/S/E3   U0       6-9e-a/22 000000aa->000000b4 Core Gen8 Desktop, Mobile, Xeon E
CFL-S        B0       6-9e-b/02 000000aa->000000b4 Core Gen8
CFL-H/S      P0       6-9e-c/22 000000a2->000000ae Core Gen9
CFL-H        R0       6-9e-d/22 000000b0->000000b8 Core Gen9 Mobile
SNB-E/EN/EP  C1/M0    6-2d-6/6d 0000061d->0000061f Xeon E3/E5, Core X
SNB-E/EN/EP  C2/M1    6-2d-7/6d 00000714->00000718 Xeon E3/E5, Core X
