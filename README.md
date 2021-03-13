## afpfs-ng for macOS / OS X

### Description

macOS / OS X ships with the ability to mount volumes via AFP. However, OS X 10.6 and newer are not capable of AFP version 2.x or older which is needed to network with Classic MacOS (7.6 to 9.2 via IP).

This version of afpfs-ng is based on Simon Vetter’s version. It has fixes ‘hacked in’ to make it work with macFUSE on macOS / OS X. As a consequence, it does not work with Fuse for Linux.

It is of use for you if you emulate Classic Mac OS, e. g. using SheepShaver or QEMU. And of course if you own an old Macintosh you want to exchange files with.

macOS / OS X already makes use of the ‘mount_afp’ command. Thus in this version of afpfs-ng that command has been changed to ‘mount_afp2’ (to indicate it is for use with AFP v. 2.x).


### Prerequesites

Download and install macFUSE from https://osxfuse.github.io/ (v. 4.0.5 as of writing this).


### Installation

Either use the .pkg installer at https://github.com/mabam/afpfs-ng-mac/releases or compile yourself as follows:

I’m not sure whether AFP up to v. 2.x offers password encryption. But I didn’t succeed in compiling it in anyway, which is why I simply disabled it:
```bash
./configure --disable-gcrypt --enable-fuse
```
```bash
make
```
```bash
sudo make install
```

Also, I couldn’t figure how to make the Fuse components compile automatically on macOS / OS X. This is how to do that manually:
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

See https://github.com/mabam/afpfs-ng-mac/releases for a version with GUI.
See https://emaculation.com/forum/viewtopic.php?f=34&p=58790#p58790 for some main issues.

If you prefer using the shell, don’t forget to load macFUSE first:
```bash
/Library/Filesystems/osxfuse.fs/Contents/Resources/load_osxfuse
```
See README_old.md for examples on commands. But mind the change to ‘mount_afp2’.

There you can also find information on the license and credits.

Credits for this macOS / OS X version goes to ‘adespoton’ for his guidance.


### Links / further reading

Information on the background and process of porting afpfs-ng to macOS / OS X can be found at http://emaculation.com/forum/viewtopic.php?f=34&p=57993#p57806 . Feel free to join the forum!
