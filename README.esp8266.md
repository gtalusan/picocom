Small hack to make picocom work with the ESP8266 custom baud rate of 74880 with OS X.

OS X has an ioctl to bypass the POSIX API.  Unfortunately tc* functions are unaware
of this, so we need to force the baud rate after going through the regular motions
of setting up the terminal.

```
$ ./picocom --imap lfcrlf -b 74880 /dev/tty.usbserial-A1044G1X 
picocom v2.2a

port is        : /dev/tty.usbserial-A1044G1X
flowcontrol    : none
baudrate is    : 74880
parity is      : none
databits are   : 8
stopbits are   : 1
escape is      : C-a
local echo is  : no
noinit is      : no
noreset is     : no
nolock is      : no
send_cmd is    : sz -vv
receive_cmd is : rz -vv -E
imap is        : lfcrlf,
omap is        : 
emap is        : crcrlf,delbs,

Type [C-a] [C-h] to see available commands

Terminal ready

 ets Jan  8 2013,rst cause:1, boot mode:(3,7)

load 0x4010f000, len 1264, room 16 
tail 0
chksum 0x42
csum 0x42
~ld
Hello World!
```
