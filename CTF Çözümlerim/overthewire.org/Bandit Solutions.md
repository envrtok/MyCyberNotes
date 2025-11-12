# 0 
ssh bandit0@bandit.labs.overthewire.org -p2220
password: bandit0

# 0 - 1
ls
cat readme

# 1 - 2
ls
cat ./-

# 2 - 3
ls
cat ./--spaces\ in\ this\ filename--

# 3 - 4
ls
cd inhere
ls 
ls -a
cat ...Hiding-From-You

# 4 - 5
ls
cd inhere
ls
find . -type f -exec file {} \

# 5 - 6
ls
cd inhere
ls
find ./* -size 1033c
cat ./maybehere07/.file2

# 6 - 7
find /  -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password

# 7 - 8
grep millionth data.txt

# 8 - 9
sort data.txt | unix -u

# 9 - 10
cat data.txt | --decode base64
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr