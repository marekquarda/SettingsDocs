https://www.tecmint.com/install-postgresql-with-pgadmin4-on-linux-mint/
# How to Install PostgreSQL with pgAdmin4 on Linux Mint 22/21/20

pgAdmin is an open-source feature-rich, frontend management tool that allows you to easily administer and manage your PostgreSQL relational database from a web browser.

It provides an easy-to-use user interface that simplifies the creation and monitoring of databases and database objects. PgAdmin 4 is an improvement of the earlier pgAdmin tool and is available for Linux, Windows, macOS systems, and even a Docker container.

In this tutorial, you will learn how to install PostgreSQL with pgAdmin4 on Linux Mint 21 and Linux Mint 20

## Step 1: Install PostgreSQL Database on Linux Mint
1. To start off, launch your terminal and update your packages using the apt package manager as shown.
```
$ sudo apt update -y
```
Once the update is complete, proceed to the next step.

Since pgAdmin4 provides a frontend interface for the management of PostgreSQL database objects, it’s essential to have PostgreSQL installed first.

2. To do this, we are going to install the postgresql package and postgresql-contrib which offers extended features that extend the functionality of PostgreSQL.
```
$ sudo apt install postgresql postgresql-contrib
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Install-PostgreSQL-on-Linux-Mint.png)
Install PostgreSQL on Linux Mint

3. Usually, PostgreSQL starts automatically on boot up. You can confirm this using the command given below:
```
$ sudo systemctl status postgresql
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Check-PostgreSQL-Status.png)
Check PostgreSQL Status

4. To log in to your PostgreSQL instance, first switch to the postgres user. The Postgres user comes included by default with the installation of PostgreSQL. Then run the psql command as shown.
```
$ sudo -i -u postgres
$ psql
# \q
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Connect-to-PostgreSQL-Shell.png)
Connect to PostgreSQL Shell

5. Additionally, you can check if the database server is accepting incoming connections as shown.
```
$ sudo pg_isready
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/PostgreSQL-Accepting-Incoming-Connections.png)
Check PostgreSQL Accepting Incoming Connections

## Step 2: Install pgAdmin4 on Linux Mint
**pgAdmin4** is available for Ubuntu 16.04 and later versions and can easily be installed using the APT package manager. The same cannot support Linux Mint and Pgadmi4 developers are yet to include support that allows users to easily install the frontend management tool using the APT package manager.

6. The only viable option is to install pgAdmin4 from a virtual environment. So first, we will install the prerequisite packages as shown.
```
$ sudo apt install libgmp3-dev build-essential libssl-dev
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Install-Prerequisite-Packages.png)
Install Prerequisite Packages

7. Next, install the Python virtual environment and associated dependencies.
```
$ sudo apt install python3-virtualenv python3-dev libpq-dev
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Install-Python-Virtual-Environment.png)
Install Python Virtual Environment

8. Next, create a directory where you will create a virtual environment.
```
$ mkdir pgadmin4 && cd pgadmin4
```
9. Then create the virtual environment as shown. Here, pgadmin4env is the name of the virtual environment.
```
$ virtualenv pgadmin4env
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Create-Virtual-Environment-for-pgAdmim4.png)

10. Once the virtual environment is in place, activate it as shown.
```
$ source pgadmin4env/bin/activate
```
11. Then use the [pip](https://www.tecmint.com/install-pip-in-linux/) tool to install pgadmin4 as shown.
```
$ pip install https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v8.11/pip/pgadmin4-8.11-py3-none-any.whl
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Install-pgadmin4-in-Linux-Mint.png)
Install PgAdmin4 in Linux Mint

12. Next, create a configuration file config_local.py.
```
-------- On Linux Mint 22/21 --------
$ sudo vim pgadmin4env/lib/python3.12/site-packages/pgadmin4/config_local.py
```
and add the lines below.
```
import os
DATA_DIR = os.path.realpath(os.path.expanduser(u'~/.pgadmin/'))
LOG_FILE = os.path.join(DATA_DIR, 'pgadmin4.log')
SQLITE_PATH = os.path.join(DATA_DIR, 'pgadmin4.db')
SESSION_DB_PATH = os.path.join(DATA_DIR, 'sessions')
STORAGE_DIR = os.path.join(DATA_DIR, 'storage')
SERVER_MODE = False
AZURE_CREDENTIAL_CACHE_DIR = os.path.join(DATA_DIR, 'azurecredentialcache')
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Create-pgadmin4-Configuration.png)
Create PgAdmin4 Configuration

13. To start the pgAdmin4 management tool, invoke the command:
```
-------- On Linux Mint 22/21 --------
$ python pgadmin4env/lib/python3.12/site-packages/pgadmin4/pgAdmin4.py
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Start-pgadmin4-Service.png)
Start PgAdmin4 Service

14. Finally, head over to your browser and browse the address shown.
```
http://127.0.0.1:5050
```
You will be prompted to set the master password, so proceed and set a strong password and click the ‘Ok’ button.
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Set-pgadmin4-Password.png)
Set PgAdmin4 Password

15. To make things easier, you can create an alias in the ~/.bashrc file as shown.
```
-------- On Linux Mint 22/21 -------- 
$ echo "alias startPg='home/marra/pgadmin4/pgadmin4env/bin/python /home/marra/pgadmin4/pgadmin4env/lib/python3.10/site-packages/pgadmin4/pgAdmin4.py'" >> ~/.bashrc

-------- On Linux Mint 20 -------- 
$ echo "alias startPg='~/pgadmin4/pgadmin4env/bin/python pgadmin4env/lib/python3.8/site-packages/pgadmin4/pgAdmin4.py'" >> ~/.bashrc
```
16. Next, update the bashrc file.
```
$ source ~/.bashrc
```
17. Finally, you can start the pgAdmin4 management tool by simply invoking the startPg command.
```
$ startPg &
```
![image](https://www.tecmint.com/wp-content/uploads/2021/01/Start-pgadmin4-Tool.png)
Start PgAdmin4 Tool

Once again head over to your browser and log in to the PgAdmin4 interface. And this concludes the installation of PostgreSQL with pgAdmin4 on Linux Mint 21 and Linux Mint 20.

