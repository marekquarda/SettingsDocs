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
//$ git remote set-url origin ssh://git@fedora:/repositories/directx11.git
git remote add origin ssh://admin@NasStation:/volume1/git-server/gittest.git
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

Dodatek 
```
# In PC TERMINAL
ssh-keygen -t ed25519
eval “$(ssh-agent -s)”
ssh-add ~/.ssh/id_ed25519

# COPY SSH publi key to NAS
ssh-copy-id -p 22  -i id_rsa.pub admin@NasStation

# EDIT File in NAS 
ssh -p [port] [admin-user]@[ip/domain]
[enter password when prompted]
sudo vim /etc/ssh/sshd_config
```












