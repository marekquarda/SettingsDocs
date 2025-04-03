https://linuxiac.com/how-to-install-docker-on-linux-mint-22/

# Step 1: Install Prerequisites
First, run the two commands below to update the package index and install the prerequisite necessary to add and use a new HTTPS repository.
```
$ sudo apt update
$ sudo apt install apt-transport-https ca-certificates curl gnupg
```
Once operations are completed, you can move to the next section, where we’ll add the Docker’s repo GPG key and repo itself to our Linux Mint 22 system.

 # Step 2: Add Docker’s Official GPG Key
Next, import the Docker GPG repository key to your Mint system. This security feature ensures that the software you’re installing is authentic.

 ```
# curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg
```
![image](https://linuxiac.b-cdn.net/wp-content/uploads/2024/08/mint22-install-docker-01.jpg)
<br>Add Docker’s repo GPG key.

Notice that the command produces no output.

# Step 3: Add Docker Repo to Linux Mint 22
After importing the GPG keys, we’ll add the official Docker repository to our Linux Mint 22 system. Thus, when a new version is released, the update package will be made available with the rest of your system’s regular updates.

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
![image](https://linuxiac.b-cdn.net/wp-content/uploads/2024/08/mint22-install-docker-02.jpg)
<br> Add the official Docker repository to Linux Mint 22. 

As with the previous command, its execution produces no output. Next, refresh the package list.
```
$ sudo apt update
```
![image](https://linuxiac.b-cdn.net/wp-content/uploads/2024/08/mint22-install-docker-03.jpg)
<br>Update the package base.

As you can see, the new Docker repository is now available to our Mint system and ready to be used.

# Step 4: Install Docker on Linux Mint 22

Finally, run the below command to install the latest up-to-date Docker release on Linux Mint 22.
```
$ sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
![image](https://linuxiac.b-cdn.net/wp-content/uploads/2024/08/mint22-install-docker-04.jpg)

This installs the following Docker components:

- docker-ce: The Docker engine itself.
- docker-ce-cli: A command line tool that lets you talk to the Docker daemon.
- containerd.io: A container runtime that manages the container’s lifecycle.
- docker-buildx-plugin: This extension for Docker enhances the capabilities of building images, mainly focusing on multi-platform builds.
- docker-compose-plugin: A configuration management plugin that helps manage multi-container Docker applications using a single YAML file.

That’s all! Docker should now be installed, service enabled, and set to start automatically on boot. In addition, check its status using the command below to confirm that everything is as expected:

```
$ sudo systemctl is-active docker
```
![image](https://linuxiac.b-cdn.net/wp-content/uploads/2024/08/mint22-install-docker-05.jpg)
<br>Check the status of the Docker service.

# Step 5: Verify Installation
```
$ sudo docker run hello-world
```
![image](https://cdn.shortpixel.ai/spai/q_lossy+ret_img+to_auto/linuxiac.com/wp-content/uploads/2024/08/mint22-install-docker-06.jpg)
<br>Docker successfully installed, up & running on Linux Mint 22.

Congratulations! As we can see, everything works properly.








