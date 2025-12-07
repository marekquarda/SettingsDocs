```
ssh-keygen 
ENTER
ENTER
ssh-copy-id orangepi@192.168.63.188
```
```
scp build/Release/test.elf orangepi@192.168.63.188
ssh orangepi@192.168.63.188
```
