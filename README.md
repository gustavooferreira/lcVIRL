OVERVIEW
========

lcVIRL stands for _live capture VIRL_ and it has the purpose to use wireshark or any other tool to capture packets on a VIRL network.


INSTALL
=======

Just copy the script to the directory you want and run it.

Or you can put it in a folder that is on your **PATH** variable, and run the script from everywhere.

For example you can create a folder **~/bin** and put the script in there as long as you add the path to this folder to your **PATH** env variable.


USAGE
=====

```
usage: lcVIRL [-h] [-v] [-c | -w] -p PORT [Virl_IP]
Options:
  -h   ---   Show this help message
  -v   ---   Show Version number
  -c   ---   Create pipe file to be listen on
  -w   ---   Capture packets with wireshark
  -p   ---   Specify port to capture packets
  Virl_IP    VIRL mgmt ip address

-----------
  Virl_IP is only optional if VIRL_HOST env variable is set!
```


**VIRL_HOST** variable can be set on your shell, so you don't need to type your VIRL mgmt ip address every single time.

For permanent definition of this env variable, you can put the export statement on your .bashrc file, like so:

```
export VIRL_HOST=172.16.100.100
```


EXAMPLES:
=========

Capture with wireshark:

```
lcVIRL -wp 10001 172.16.100.100
```

If you have **VIRL_HOST** defined and exported on your shell, you can simply run:

```
lcVIRL -wp 10001
```

To create a pipe file to "plug" other applications like tcpdump, you can do:

```
lcVIRL -cp 10001 172.16.100.100

```

and to make tcpdump listen on that pipe file:

```
tcpdump -r /tmp/live_capture_10001_28460
```


NOTES
=====

 - You can sniff multiple ports with multiple instance of this script.
   - If you are using -c flag, it will create a pipe with a different name every time.
 - When using -c flag, if you have xclip installed, the script will put the filename in the clipboard, so you can simply paste it where you want.
 - The -c flag can be used to connect tcpdump or other software that has the capability to receive packets from a pipe or read a pcap file.


LICENSE
=======

This script is under the terms of MIT License. Have a look at LICENSE for more information.
