---
layout: post
title:  "The Sleuth Kit"
date:   2024-12-23 12:59:42 +0000
categories: forensics
---
<b>File carving</b> is the process of recovering access to files that have been corrupted, partially lost, deleted, or inaccessible due to partition structure damage. To demonstrate file carving, a Virtual Lab environment was created running a Kali Linux virtual machine, which came preinstalled with a number of excellent tools for performing digital forensics, namely the very powerful, and free [testdisk][tdl] open-source utility, and the [Sleuth Kit][skl], a collection of command-line tools that can be used to analyse and recover files from disk images. Anyone wishing to evaluate the software and practice their digital forensics skills are encouraged to try these tools out! There are also a number of freely downloadable test images to play with, available from the [Digital Forensics Tool Testing Images repository][dftl].

[tdl]: https://www.cgsecurity.org/wiki/TestDisk
[dftl]: https://dftt.sourceforge.net/
[skl]: https://sleuthkit.org/index.php

Some useful Sleuth Kit commands are:
- istat: useful for pulling inode information from a hidden partition. An <b>inode</b> is a file system metadata structure that is used to store and organise file object information (e.g., file size, owner user, permissions, and timestamps.
- mmls: can be used to determine the layout of a disk, including offsets of any hidden partitions and unallocated space.
- tsk_recover: can automatically recover deleted files from drive images, copying them to a local directory.
- fls: useful for pulling information from hidden partitions, and listing allocated and deleted file names.
- fsstat: can be used for displaying details of the file system(s) on a drive image.

  
