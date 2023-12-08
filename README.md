arkfind
=======

A utility to recursively search for files by name in a filesystem, also looking
inside archives to an arbitary depth.

Supported archives are: TAR, TAR.GZ, TAR.BZ2 and ZIP. It should also work on
ZIP-like archives such as JAR files. There are options for case sensitivity,
glob-style pattern matching and JSON output. Non-ASCII character sets should be
supported, although there may be some issues with command line encodings if they
aren't UTF-8 (and there's also the fact that ZIP files don't have a universally
accepted encoding).

The script uses the "magic" library to determine file types, so it doesn't rely
on file extensions to identify archives.

Dependencies and installation
-----------------------------

Download the "arkfind" script. Make it executable to run it like ```./arkfind```
 or run it with ```python ./arkfind```.

Dependencies:

  * Python (>= 2.7)
  * python-magic (>= 0.4.3) (installable via pip)

Examples
--------

Say that over years of different backup regimes and ad-hoc archiving you've
ended up with TAR files inside ZIP files, and there are many such ZIP files all
inside one big TAR.BZ2 file. You want to find a file called "magic.txt", so you
use the script like so:

```bash
$ arkfind AllBackups.tar.bz2 "magic.txt"
AllBackups.tar.bz2
  > backups_2006/lab_pc/MISC.zip
	  > misc_lab_stuff/magic.txt
```
        
Maybe you have a directory full of such archives, and you can't remember the
whole name of the file. You can do this:

```bash
$ arkfind -g backups/ "magic*.*"
backups/backup_2007.zip
  > 06/magic_june_2007.rtf
backups/backup_2008.zip
  > 01/magic_jan_2008.html
```
