### Backup the data
The ``rsync`` command is used to synchronize entire directory trees. Basically, it copies file as the ``cp`` command does. In addition, ``rsync`` checks if the file being copied already exists. If the file exists and there is no change in size or modification time, ``rsync`` will avoid an unnecessary copy and save time. Furthermore, because rsync copies only the parts of files that have actually changed, it can be very fast.

The ``rsync`` is very efficient when recursively copying one directory tree via network, because only the differences are transmitted. One often synchronizes the destination directory tree with the origin, using the  ``rsync -r`` option to recursively walk down the directory tree copying all files and directories below the one listed as the source.

```
# rsync -ravzh project_ABC /data/backups
sending incremental file list
project_ABC/
project_ABC/file1.txt
project_ABC/file2.txt
project_ABC/file3.txt
project_ABC/file4.txt

sent 636 bytes  received 92 bytes  1.46K bytes/sec
total size is 452  speedup is 0.62

```

### Compress the data
File data is often compressed to save disk space and reduce the time it takes to transmit files over networks. Linux uses a number of methods to perform this compression.

| Command | Usage                                                                                                                           |
|---------|---------------------------------------------------------------------------------------------------------------------------------|
| gzip    | The most frequently used Linux compression utility                                                                              |
| bzip2   | Produces files significantly smaller than those produced by gzip                                                                |
| xz      | The most space efficient compression utility used in Linux. It is now used by kernel.org to store archives of the Linux kernel. |
| zip     | Is often required to examine and decompress archives from other operating systems                                               |
| zstd    | A fast compression algorithm that provides high compression ratios                                                              |

These techniques vary in the efficiency of the compression (how much space is saved) and in how long they take to compress; generally the more efficient techniques take longer. Decompression time doesn't vary as much across different methods.

### Archiving data
The ``tar`` command allows you to create or extract files from an archive file, often called a tarball. At the same time you can optionally compress while creating the archive, and decompress while extracting its contents.

Here are some examples of the use of tar:

| Command                      | Usage                                                           |
|------------------------------|-----------------------------------------------------------------|
| tar xvf mydir.tar            | Extract all the files in mydir.tar into the mydir directory     |
| tar zcvf mydir.tar.gz mydir  | Create the archive and compress with gzip                       |
| tar jcvf mydir.tar.bz2 mydir | Create the archive and compress with bz2                        |
| tar xvf mydir.tar.gz         | Extract all the files in mydir.tar.gz into the mydir directory. |
| tar cvf  mydir.tar           | show the content into the mydir directory                       |
