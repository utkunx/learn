https://askubuntu.com/questions/371261/display-monitor-info-via-command-line


[utku2@ffyf ~]$ xrandr --verbose | edid-decode
EDID version: 1.4
Manufacturer: AUO Model 32eb Serial Number 0
Made in week 37 of 2017
Digital display
8 bits per primary color channel
DisplayPort interface
Maximum image size: 34 cm x 19 cm
Gamma: 2.20
Supported color formats: RGB 4:4:4
First detailed timing includes the native pixel format and preferred refresh rate
Display x,y Chromaticity:
  Red:   0.6445, 0.3359
  Green: 0.3105, 0.6064
  Blue:  0.1523, 0.0488
  White: 0.3134, 0.3291
Established timings supported:
Standard timings supported:
Detailed mode: Clock 533.300 MHz, 344 mm x 193 mm
               3840 3888 3920 4000 hborder 0
               2160 2163 2168 2222 vborder 0
               -hsync -vsync 
               VertFreq: 60 Hz, HorFreq: 133325 Hz
Manufacturer-specified data, tag 15
ASCII string: AUO
ASCII string: B156ZAN03.2 
Checksum: 0xd (valid)

Lenovo LEN40BE (LB156ZAN03.2);

Lenovo LEN40BE (LB156ZAN03.2);


%TPWUHDF%   = TPLCDWUHDF_40BE.Install.NTx86,    Monitor\LEN40BE   ; 15.6" Wide UHD   16:9  IPS          3840x2160   F, DolbyVision, 400nit (AUO)


for 500 nit oled

%TPWUHDO%   = TPLCDWUHDO_4141.Install.NTx86,    Monitor\LEN4141   ; 15.6" Wide UHD   16:9  OLED         3840x2160   O, DolbyVision, 400nit (SDC)

----

back to

[TPLCDWUHDF_40BE.Install.NTx86]        ; Wide UHD 16:9 3840x2160 IPS, DolbyVision, 40BE(AUO)
DelReg=DEL_CURRENT_REG
AddReg=HD3840, DPMS, ICM_40BE
CopyFiles=TPLCD.CopyFiles


[ICM_40BE]
HKR,,ICMProfile,0,"TPLCD_40BE.icm"
HKR,,ICMProfileAC,0,"TPLCD_40BE.icm"