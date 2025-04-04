https://www.tecmint.com/install-postgresql-with-pgadmin4-on-linux-mint/

# Step 1: Install PostgreSQL Database on Linux Mint
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
Check PostgreSQL Status
4. To log in to your PostgreSQL instance, first switch to the postgres user. The Postgres user comes included by default with the installation of PostgreSQL. Then run the psql command as shown.
```
$ sudo -i -u postgres
$ psql
# \q
```

Connect to PostgreSQL Shell
5. Additionally, you can check if the database server is accepting incoming connections as shown.
```
$ sudo pg_isready
```
Check PostgreSQL Accepting Incoming Connections
# Step 2: Install pgAdmin4 on Linux Mint
pgAdmin4 is available for Ubuntu 16.04 and later versions and can easily be installed using the APT package manager. The same cannot support Linux Mint and Pgadmi4 developers are yet to include support that allows users to easily install the frontend management tool using the APT package manager.

6. The only viable option is to install pgAdmin4 from a virtual environment. So first, we will install the prerequisite packages as shown.
```
$ sudo apt install libgmp3-dev build-essential libssl-dev
```
Install Prerequisite Packages
7. Next, install the Python virtual environment and associated dependencies.
```
$ sudo apt install python3-virtualenv python3-dev libpq-dev
```
