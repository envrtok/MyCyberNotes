## 🔐 Level Goal

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

---

## 🛠️ Solution

```bash
mkdir ../../tmp/banditwork
cd ../../tmp/banditwork
cp ../../home/bandit12/data.txt data.hex
xxd -r data.hex > data.bin
file data.bin
mv data.bin data.bin.gz
gzip -d data.bin.gz
file data.bin
mv data.bin data.bin.bz2
bzip2 -d data.bin.bz2
file data.bin
mv data.bin data.bin.gz
gzip -d data.bin.gz
file data.bin
mv data.bin data.bin.tar
tar -xvf data.bin.tar
file data5.bin
mv data5.bin data5.bin.tar
tar -xvf data5.bin.tar
file data6.bin
mv data6.bin data6.bin.bz2 
bzip2 -d data6.bin.bz2
file data6.bin
mv data6.bin data6.bin.tar
tar -xvf data6.bin.tar
file data8.bin
mv data8.bin data8.bin.gz
gzip -d data8.bin.gz
file data8.bin
cat data8.bin
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```