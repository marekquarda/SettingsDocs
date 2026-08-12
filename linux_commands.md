SMART disk information 
-- no need to install application 
```
sudo smartctl -a /dev/sdc
```
STRESS test
-- note: include memory test, SSD test 
```
sudo dnf install stressapptest
stressapptest -s 36000
```
