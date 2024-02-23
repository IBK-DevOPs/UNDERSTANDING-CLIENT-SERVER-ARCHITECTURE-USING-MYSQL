# IMPLEMENT A CLIENT SERVER ACHITECTURE USING MYSQL DATABASE MANAGEMENT

### UNDERSTANDING CLIENT-SERVER ARCHITECTURE

#### Client – Server architecture With MYSQL
#### Client server means architecture in which 2 or more computer are connected together over a network to send and receive request between one another. 
#### During this communication each machine has its own role.
#### The machine sending request is known as Client
#### The machine responding (serving) is called server

### Let’s open our ubuntu terminal.
### Input below command
`$ curl -Iv www.propitixhomes.com`

![alt text](image-1.png)


## Traceroute
### A traceroute works by sending Internet Control Message Protocol (ICMP) packets, and every router involved in transferring the data gets these packets. The ICMP packets provide information about whether the routers used in the transmission are able to effectively transfer the data.
### In computing, traceroute and tracert are computer network diagnostic commands for displaying possible routes (paths) and measuring transit delays of packets.

## Ping
### ping is a computer network administration software utility used to test the reachability of a host on an Internet Protocol network. It is available for virtually all operating systems that have networking capability, including most embedded network administration software.

## MYSQL Basic Command
### •	SELECT - extracts data from a database.
### •	UPDATE - updates data in a database.
### •	DELETE - deletes data from a database.
### •	INSERT INTO - inserts new data into a database.
### •	CREATE DATABASE - creates a new database.
### •	ALTER DATABASE - modifies a database.
### •	CREATE TABLE - creates a new table.

### TO IMPLEMENT A CLIENT SERVER ACHITECTURE USING MYSQL DATABASE MANAGEMENT

### Create and configure 2 Linux based servers [ec2 instance]
### Follow below steps

![alt text](<Image/Mysql server on EC2.png>)
![alt text](<Image/mysql server A.png>)

### 1	Create and configure 2 linux base virtual server by using EC2 instance AWS
![alt text](<Image/Client server on EC2.png>)


### 2	Install mysql-client software on a client server (B) Firstly run sudo apt-get update
![alt text](<Image/Install mysql on client server.png>)



### Then run `sudo apt install mysql-client`

### 3	Install MYSQL software on mysql server (sever A) 
### Firstly run sudo mysql
### Then run sudo apt install mysql-server
![alt text](<Image/install mysql on mysql server.png>)


### 4	Use local IP address for server A to connect to client server. Create new security rule with MYQSL sever TCP port 3306R
### Make mysql executable by running

![alt text](<Image/inbound rule  server private IP of mysql client on mysql.png>)


![alt text](<Image/Input client IP on mysql.png>)


### On EC2 for server A create new security rule with mysql server TCP 3306 with local IP

![alt text](<Image/mysql server port 3306.png>)


### 5	Configure Mysql server (server A)
### Make mysql executabme
### Run `Sudo systemctl restart mysql`
### `sudo mysql_secure_installation`
### Create user for remote user
### Create data base for remote user
### `CREATE USER1 'remote_user'@'%' IDENTIFY
### WITH mysql_native_password BY 'password';
![alt text](<Image/create new user for client.png>)

### `CREATE DATABASE test_db;
![alt text](<Image/create database.png>)

#### We have below output
### `Query OK, 0 rows affected (0.01 sec)`
#### Exit MYSQL

![alt text](<Image/secure mysql.png>)
![alt text](<Image/Grant all privileges.png>)

### After Mysql server configuration run mysql script
### With below code.
### `sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`
### Then replace IP 127.0.0.1 to 0.0.0.0 .
### Save and close
### Run `sudo systemctl restart mysql`

### Run `sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf  edit 127.0.0.1 to 0.0.0.0`
![alt text](<Image/mysql server database.png>)


### 6	From mysql client connect to mysql server data base without using ssh private IP of  MYSQL server 
    `sudo mysql -u remote_user1 -h 172.31.5.116 -p`
![alt text](<Image/link host server with client with host IP address.png>)


7   `sudo mysql -u remote_user1 -h 172.31.5.116 -p`
### Enter created user1 password 
### We have below message

### `Welcome to the MySQL monitor.  Commands end with ; or \g.
### Your MySQL connection id is 8
![alt text](<Image/Show data base (successfully connected.png>)


`Server version: 8.0.36-0ubuntu0.22.04.1 (Ubuntu)`

`Copyright (c) 2000, 2024, Oracle and/or its affiliates.`

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners`. 

input `Show databases`;
We have below result
mysql> Show databases;

`+--------------------+
| Database           |
+--------------------+
| information_schema |
| performance_schema |
+--------------------+
2 rows in set (0.02 sec)`

![alt text](<Image/to show that the project is completed.png>)


![alt text](<Image/A web Client server pix.png>)


























