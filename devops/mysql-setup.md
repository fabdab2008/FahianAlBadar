# Overview: Installing MySQL 8, MySQL YOG, and Creating a Dedicated User

This task involves setting up **MySQL 8** on a Linux-based virtual machine, securing the database server, and configuring access for external tools such as **MySQL YOG** (a GUI client). The process includes adding the official MySQL APT repository, installing the MySQL server, and performing post-installation security hardening.

Additionally, a **dedicated MySQL user** is created with **restricted privileges** and **remote access**, which is a best practice for enhancing security—especially when managing databases across networks. Configuration steps also ensure the database listens on external interfaces and that the system firewall allows MySQL traffic.

The end goal is to enable secure, remote access to the MySQL server using a GUI client like MySQL YOG, suitable for both development and administrative tasks.

---

## Step-by-Step Instructions

### 1. Update Package Info
```bash
sudo apt update
sudo apt upgrade -y
```

### 2. Add MySQL APT Repository
```bash
wget https://dev.mysql.com/get/mysql-apt-config_0.8.24-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.24-1_all.deb
```

### 3. Update Package Info Again
```bash
sudo apt update
```

### 4. Install MySQL Server
```bash
sudo apt install mysql-server -y
```

### 5. Secure Your MySQL Installation
```bash
sudo mysql_secure_installation
```

### 6. Check MySQL Service Status
```bash
sudo systemctl status mysql
```

---

## Creating a Dedicated MySQL User with Remote Access

> Creating a dedicated MySQL user with remote access and limited privileges is much more secure than enabling remote root login.

### 1. Log into MySQL as Root
```bash
mysql -u root -p
```

### 2. Create a New MySQL User
```sql
CREATE USER 'myuser'@'192.168.71.1' IDENTIFIED BY 'mypassword';
-- Or for access from any host (for testing only)
CREATE USER 'myuser'@'%' IDENTIFIED BY 'mypassword';
```

### 3. Grant Necessary Privileges
```sql
-- Access only to a specific database
GRANT SELECT, INSERT, UPDATE, DELETE ON mydb.* TO 'myuser'@'192.168.71.1';

-- OR: Full access (less secure)
GRANT ALL PRIVILEGES ON *.* TO 'myuser'@'192.168.71.1';
```

### 4. Apply Changes
```sql
FLUSH PRIVILEGES;
```

### 5. Configure MySQL to Listen on All IPs
```bash
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
Find the line:
```
bind-address = 127.0.0.1
```
Change it to:
```
bind-address = 0.0.0.0
```

Then restart MySQL:
```bash
sudo systemctl restart mysql
```

### 6. Allow MySQL Traffic Through the Firewall
```bash
sudo ufw allow 3306
```

### 7. Connect from MySQL YOG Using:
- **Host/IP**: the VM's IP address  
- **Username**: `myuser`  
- **Password**: `mypassword`  
- **Port**: `3306`
