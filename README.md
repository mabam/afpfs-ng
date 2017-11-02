## afpfs-ng for macOS / OS X

### Description

macOS / OS X ships with the ability to mount volumes via AFP. However, OS X 10.6 and newer are not capable of AFP version 2.x or older which is needed to network with Classic MacOS (7.6 to 9.2 via IP).

This version of afpfs-ng is based on Simon Vetter's version. It has fixes 'hacked in' to make it work with Fuse for macOS / OSXFUSE on macOS / OS X. As a consequence, it does not work with Fuse for Linux.

It is of use for you if you emulate Classic MacOS, e.g. using SheepShaver or QEMU. And of course if you own an old Macintosh you want to exchange files with.

macOS / OS X already makes use of the 'mount_afp' command. Thus in this version of afpfs-ng that command has been changed to 'mount_afp2' (to indicate it is for use with AFP v. 2.x).


### Prerequesites

Download and install Fuse for macOS from https://osxfuse.github.io/ (v. 3.7.1 as of writing this). The Fuse compatibility layer is NOT required.


### Installation

AFP up to v. 2.x does not offer password encryption which is why we simply disable it rather than installing gcrypt on macOS / OS X first:
```bash
./configure --disable-gcrypt --enable-fuse
```
```bash
make
```
```bash
sudo make install
```

Also, I couldn't figure how to make the fuse components compile automatically on macOS / OS X. This is how to do that manually:
```bash
cd fuse
```
```bash
make
```
```bash
sudo make install
```


### Usage, credits and license

Don't forget to load Fuse for macOS first:
```bash
/Library/Filesystems/osxfuse.fs/Contents/Resources/load_osxfuse
```
See README_old.md for examples on commands. But mind the change to 'mount_afp2'.

There you can also find information on the license and credits.

Credits for this macOS / OS X version goes to 'adespoton' for his guidance.


### Links / further reading

Information on the background and process of porting afpfs-ng to macOS / OS X can be found at http://emaculation.com/forum/viewtopic.php?f=34&p=57993#p57806 . Feel free to join the forum!
