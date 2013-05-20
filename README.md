arkfind
=======

A utility to recursively search for files by name in a filesystem, also looking
inside archives to an arbitary depth.

Say, for example, over years of different backup regimes and ad-hoc archiving
you've ended up with TAR files inside ZIP files, and there are many such ZIP
files all inside one big TAR.BZ2 file. You want to find a file called
"magic.txt", so you use the script like so:

    $ arkfind AllBackups.tar.bz2 "magic.txt"
    AllBackups.tar.bz2
      > backups_2006/lab_pc/MISC.zip
          > misc_lab_stuff/magic.txt
        
Supported archives are: TAR, TAR.GZ, TAR.BZ2 and ZIP. There are options for case
sensitivity, glob-style pattern matching and JSON output. Non-ASCII character
sets should be supported, although there may be some issues with command line
encodings if they aren't UTF-8 (and there's also the fact that ZIP files don't
have a universally accepted encoding).