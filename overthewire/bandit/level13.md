# Level 12 -> Level 13
The goal of this level is to find the password stored in the `data.txt` file, which is a hexdump of a file that has been repeatedly compressed.

To begin decompressing the file, we first must revert the hexdump that it was made into. We will do this by using the command:

`xxd -r data.txt`

We will notice that the command will simply output to the terminal. In this instance, we actually want it in a file since we know that the hexdump was compressed so we can begin decompressing. We will do this by piping/redirecting the output to a separate file.

`xxd -r data.txt > data1.txt`

Next we must repeatedly use the `file` command to observe the file's properties:

`file data1.txt`

With the output being:

`data1.txt: gzip compressed data, was "data2.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 578`

Letting us know that we now must use the `gzip` command to begin decompressing. This is done with the `-d` parameter to signify decompression and the `-S` parameter to specify the filename extension:

`gzip -d -S .txt data1.txt`

This will turn the `data1.txt` file into a `data1` file which, when `file` is used on it, will output:

`data1: bzip2 compressed data, block size = 900k`

Once again, signifying that we must now use the `bzip2` or `bzcat` command:

`bzcat data1 > data2`

We `file` data2:

`data2: gzip compressed data, was "data4.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 20480`

We use the `zcat` command since the `data2` file doesn't have a filename extension:

`zcat data2 > data3`

We `file` data3:

`data3: POSIX tar archive (GNU)`

And use the `tar` command to extract the `data3` file:

`tar --extract --file data3`

Netting us `data5.bin`, which is again a `POSIX tar archive (GNU)`, so we use the same command:

`tar --extract --file data5.bin`

Resulting in `data6.bin` which is `bzip2 compressed data` needing the command:

`bzcat data6.bin > data7`

Resulting in `data7` being another `POSIX tar archive (GNU)` needing the command:

`tar --extract --file data7`

Resulting in `data8` which is a `gzip compressed data` needing the command:

`gzip -d -S .bin data8.bin`

Finally, we can `cat` the `data8` file, resulting in the output:

`The password is qQYQiHOBPR8zR61qxYqX45quvihF2uzk`
