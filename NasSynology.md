https://github.com/007revad/Synology_SSH_key_setup

# Add Git to NAS. 
Generate public key on Windows side
```
# ssh-keygen -o
```
Enter, Enter, no password 
open powershell 
```
# cat ~/.ssh/id_rsa.pub
```
Check if volume1/homes exists
>> enable user home service (DSM - Control Panel - Users - Advanced - User Home)

Copy (CTRL+C)
Open SSH Nas server 
```
# cd /volume1/homes/admin/.ssh    // or make dir .ssh
# vim autorized_keys
```
Past (CTRL+V)
Save VIM.

# Git configure 
Open SSH connection to NAS Synology
```
cd /volume1/git-server/
git init --bare new-git-repo.git
```
Open repo to change
```
//$ git remote set-url origin ssh://admin@NasStation:/volume1/git-server/new-git-repo
git remote add master ssh://admin@NasStation:/volume1/git-server/gittest.git
git fetch
git push
git push --set-upstream master master
$ git config --global user.email "mquarda@centrum.cz"
$ git config --global user.name "Marek Xara Quarda"
```

Test clone 
```
git clone ssh://admin@NasStation:/volume1/git-server/new-git-repo.git
```
Info remote repo
```
git remote -v
```
View the S.M.A.R.T.
```
sudo smartctl -a -d sat /dev/sda
```













