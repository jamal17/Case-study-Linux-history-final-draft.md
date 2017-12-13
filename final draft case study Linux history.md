#How Linux Works: What Every Superuser Should Know Case Study: History of UNIX Final Draft



The birth of Linux and the stages of the development over the very short time. Why Linux is more useful today than windows system.

Linux is one of the most important innovations in information technology today, today Linux deliver the information
through the Internet with very high speed, as most internet servers, such as Google, Facebook, and Twitter use Linux system. Linux 
is an extension of the UNIX system, but is complementary to it. If we go back, in 1969, where the AT&T create an operating system with 
open source, and free with no charge where any user can look at the code, which allows them to developing according to their needs,
it’s become a very popularity inside the university where the students could develop this system and make it more effective.  

However, AT&T impose the fee on the second edition of UNIX. This fee prompting the universities students to innovate
the UNIX system to be more effective and free of charge. In 1983, the American student Richard Stallman
could develop and create a project that can convert all closed source to open source he called it GNU,
but could not complete it because he missed the kernel the heart of the operating system. In 1991, in the other
side of the world, a young man university student Linus Benedict Torvalds in a small country, Finland, invented
the kernel or the heart of the operating system, where it was open source and
free, he called Linux. 

 
EXT filesystem history

It is true that the EXT file system was written for Linux systems, but its roots are rooted in the Minix operating system and 

its file system, which is five years ahead of Linux, first published in 1987.

It will make it easier to understand the EXT4 file system if we look at the overall history of the EXT file system and the  technical
development that has taken place for the EXT file family from its origins in the Minix system.

When Linus Torvalds wrote the Linux kernel, he needed a file system but did not want to write one, so he included in the 

Minix file system written by Andrew S. Tanenbaum and was part of the Minix operating system, which is an Unix-like 

operating system written for educational purposes, and his source chip was available free of charge and licensed with a  license
allowed to include in the first version of the Linux kernel.

This is the structure of the Minix file system, the majority of which resides in the partition that uses the previous file system:

The boot sector in the first sector on the hard drive containing the file system; the boot sector has a very small boot record as 
well as the partition table.
The first sector in each section is called the superblock sector, which contains metadata that identifies the other structures 
in the file system and locates
them in the physical disk.
Asector in the index list (inode), which determines which indexes are used and available for use.

Indexing indexes, which have disk space, and each index index that has information about a single file, including the location of data 
blocks, which areas on the disk are associated with that file.
A list of regions (zone bitmap), which tracks the data areas used and free.

Datastorage area (date zone), the place where data is stored.

The bitmap is used to represent a single data area or index; if the bit value is zero, the storage area or the index is free and 
can be used, but if the bit value is equal to one, then the data area or index in use.

Well, what is the index? This is the abbreviation of index-node, since indexing index is a 256-byte disk block that stores data
describing the file.This data includes the size of the file, the user ID of the owner of the file and the owner group, as well as the 
file style.

Three timestamps that specify the time and date that the file was last accessed, when modified, and when the data in the index
changes last time. The Indexing contains information indicating where the file data is stored on the hard drive, which is a list of 
data areas (or blocks) in the Minix and EXT1-3 file systems.
The Minix file indexing index supports storing nine blocks of data, seven of which are direct and two are not direct.

EXT2

The EXT2 file system was very successful.  

It was used in Linux distributions for many years.

It was introduced in 1993. Developed by Rémy Card.

The EXT2 file system had the metadata structure in the EXT file system itself, but the EXT2 file system was looking ahead,  leaving
a lot of space between the metadata structures for future use.
As with the Minix file system, EXT2 has a boot sector in the first sector on the hard drive on which it was installed, which has
a very small boot record and partition table, and there was a reserved space after the boot sector, which extends from the boot
sector to the first partition on the hard drive.

The GRUB2 boot loader (or GRUB1) uses this space to store its boot code.

The space in each EXT2 partition is divided into cylinder groups that allow for granular management of storage space. 

The EXT file system implements data distribution strategies that reduce file fragmentation as much as possible and reduce fragmentation
will improve file system performance.  Maximum individual file size can be from 16 GB to 2 TB.

Overall ext2 file system size can be from 2 TB to 32 TB.

EXT3

In 2001 Stephen Tweedie introduced the EXT3, he was the first one working on extending ext2 in Journaling the Linux ext2 fs 
Filesystem in a 1998, and later in a February 1999 kernel mailing list posting. 

The filesystem was merged with the mainline Linux kernel in November 2001 from 2.4.15 onward.

The EXT3 file system had the sole purpose of overcoming the problem of fsck taking a long time to restore the damaged  disk
structure due to an improper closure that occurred during an update of a file. 
The only change to the EXT file system was the addition of records or journals the modifications are stored before they are executed
on the file system; the rest of the disk structure remains identical to the EXT2 file system structure.
Instead of writing data to disk datastores directly as in earlier versions, the records in the EXT3 file system write the file data
- in addition to the metadata - to a specific location on the disk, and after the data is safely written to the disk, it can be merged
or added to the target file is likely to lose data by near zero.

After the data is written to the data blocks on the disk, the journal will be updated so that the file system remains stable in the
event of a system failure before writing all the data in the registry on the disk.

There are three types of journaling available in ext3 file system.

1.Journal – Metadata and content are saved in the journal.

2.Ordered – Only metadata is saved in the journal. Metadata are journaled only after writing the content to disk. This is the default.

3.Writeback – Only metadata is saved in the journal. Metadata might be journaled either before or after the content is written to
the disk.
The file system will check for conflicts on boot, and the data in the registry will write to the data blocks on the disk to complete
updates targeting a file.

Logging reduces the performance of data writing, but there are three options available for records that allow a user to choose
between performance, data integrity, and protection.
The records feature reduces the time needed to scan the hard drive and look for conflicts after hours (or even days) from a few
minutes (in most cases).
The existing EXT2 file system can be updated to EXT3 by adding a journal using the following command:
tune2fs -j / dev / sda1

Where / dev / sda1 is the disk ID and partition we want to update; make sure to modify the file system type by modifying the
flag type in the / etc / fstab file and reconnecting that partition or rebooting the system to adjust.

The Maximum individual file size can be from 16 GB to 2 TB.

On the Overall ext3 file system size can be from 2 TB to 32 TB.

EXT4

The EXT4 file system it was introduced in 2008, EXT4 improves performance, reliability and storage capacity. 

To improve the reliability of mission-critical systems, the time stamps of the file system have been improved to make them  accurately
stored up to nanoseconds, and the problem of "2038" has been resolved until 2446.

The data reservation mechanism is transformed from fixed-sized blocks to extents. 

The extension can be described as the beginning and end of a place on the hard drive. 

This makes it possible to characterize long and continuous files in a single index, which reduces the number of indicators required
to describe a place Store all data in large files; the EXT4 file system implements data distribution strategies that minimize
fragmentation of the file.
The EXT4 file system reduces file fragmentation by making newly created files on the disk and not bundled in a single  place
at the beginning of the disk as old file systems did.
File space reservations attempt to store files as regularly as possible on the cylindrical collections. 

If the file is necessary to be fragmented, we will try to make those pieces physically close to reduce the delay time caused by
the read head movement.
There are other strategies used to store more storage space than when creating new files or adding data to pre-existing files, this
helps increase the file space without breaking it into more than one part; Fragmentation of existing files.

The EXT4 file system uses several strategies, such as space delay, to allow the file system to collect all the data that will be  
written to the disk before reserving storage space, thus improving the possibility of storing contiguous or persistent storage space.

Old EXT file systems such as EXT2 and EXT3 can be mounted as EXT4 file system to improve performance a bit, but this means disabling 
some of the most important new features of the EXT4 file system, so it is not recommend doing so.

Maximum individual file size can be from 16 GB to 16 TB

Overall maximum ext4 file system size is 1 EB (exabyte). 1 EB = 1024 PB (petabyte). 1 PB = 1024 TB (terabyte).

Directory can contain a maximum of 640,000 subdirectories (as opposed to 32,000 in ext3).

In EXT4, we have the option of turning the journaling feature “of”.

To creating an ext2, or ext3, or ext4 filesystem.

Once we’ve partitioned our hard disk using command, we use mke2fs to create either ext2, ext3, or ext4 file system.

Create an ext2 file system:

$ mke2fs /dev/sda1

Create an ext3 file system:

$ mkfs. ext3 /dev/sda1

Or

$ mke2fs -j /dev/sda1

Create an ext4 filesystem:

$ mkfs. ext4 /dev/sda1

Or

$ mk2fs -t ext4 /dev/sad1

How to convert between them, and the commands we will use for them:

How to convert ext2 to ext3 For example, if you are upgrading /dev/sda2 that is mounted as /home, from ext2 to ext3, do the following.

$ unmount /dev/sad2

$ tune2fs -j /dev/sda2

$ mount /dev/sad2 /home

How converting ext3 to ext4

If we are upgrading /dev/sda2 that is mounted as /home, from ext3 to ext4, we have to do the following.

$ unmount /dev/sda2

$tune2fs -o extents, uninit_bg,dir_index /dev/sda2

$ e2fsck -pf /dev/sda2

$ mount /dev/sda2 /home

**Warning**:

We must try all above commands only on the test system, otherwise we will lose all our data.



References

David, Both. An introduction to Linux EXT4 filesystem, Open source.com. 25 May 2017,
    https://www.opensource.com/article/17/5/introduction-ext4-filesystem

NATARAJAN, RAMESH. Linux File Systems: Ext2 vs Ext3 vs Ext4. 16 May 2011,
    www.thegeekstuff.com/2011/05/Ext2-Ext3-Ext4/.

 


