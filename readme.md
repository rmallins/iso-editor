# What is it?
A command line tool that mounts an ISO to a writeable location. After that data has been modified it creates a new bootable ISO from it in the current directory.

# Usage examples

## Online help

```
$ ./iso-editor -h
usage: iso-editor <path to iso to edit>
version: 0.9.0

Mounts the iso to a writeable location then pauses while you edit
the data.

Press <ctrl-C> at this point to abort without generating an ISO.

After edits are complete, press <return> to generate a new ISO
in the current directory from the edited data.

Rather than extract the ISO this script mounts the ISO as the lower
layer of an overlay filesystem to allow edit while minimising disk
space requirements.
$ 
```

## Editing session

```
    rmallins@rmallins-Latitude-E6530:/src/iso-editor$ ls
    iso-editor  ubuntu-22.04.5-live-server-amd64.iso
    rmallins@rmallins-Latitude-E6530:/src/iso-editor$ ./iso-editor ./ubuntu-22.04.5-live-server-amd64.iso
    ISO data is mounted to:
       /tmp/iso-editor/iso_mnt
    Edit data as desired and once done, press <Return> to build ISO from the edited data.
    Press <ctrl>-C to abandon the operation.

<edit data here>

    generating ubuntu-22.04.5-live-server-amd64.iso.edited.iso ...
    xorriso 1.5.6 : RockRidge filesystem manipulator, libburnia project.

    Drive current: -outdev 'stdio:ubuntu-22.04.5-live-server-amd64.iso.edited.iso'
    Media current: stdio file, overwriteable
    Media status : is blank
    Media summary: 0 sessions, 0 data blocks, 0 data,  164g free
    Added to ISO image: directory '/'='/tmp/grub.65Dors'
    xorriso : UPDATE :     596 files added in 1 seconds
    Added to ISO image: directory '/'='/tmp/iso-editor/iso_mnt'
    xorriso : UPDATE :    1438 files added in 1 seconds
    xorriso : NOTE : Copying to System Area: 512 bytes from file '/usr/lib/grub/i386-pc/boot_hybrid.img'
    libisofs: NOTE : Automatically adjusted MBR geometry to 1019/128/32
    xorriso : UPDATE :  2.67% done
    xorriso : UPDATE :  16.08% done
    xorriso : UPDATE :  42.37% done
    xorriso : UPDATE :  60.58% done, estimate finish Tue Jul 15 21:23:38 2025
    xorriso : UPDATE :  84.66% done
    ISO image produced: 1042465 sectors
    Written to medium : 1042465 sectors at LBA 0
    Writing to 'stdio:ubuntu-22.04.5-live-server-amd64.iso.edited.iso' completed successfully.

    Generation of ubuntu-22.04.5-live-server-amd64.iso.edited.iso successful.
    umount /tmp/iso-editor/iso_mnt
    umount /tmp/iso-editor/lower
    rmallins@rmallins-Latitude-E6530:/src/iso-editor$

<new iso can be seen in CWD with ".edited.iso" suffix>

    rmallins@rmallins-Latitude-E6530:/src/iso-editor$ ls
    iso-editor  ubuntu-22.04.5-live-server-amd64.iso  ubuntu-22.04.5-live-server-amd64.iso.edited.iso
    rmallins@rmallins-Latitude-E6530:/src/iso-editor$
```
