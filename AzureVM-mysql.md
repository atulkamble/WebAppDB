# 📘 MySQL Installation & Configuration on Azure VM

**(Ubuntu Linux & Windows | NSG Port 3306)**

---

## 1️⃣ Overview

This document explains how to:

* Install **MySQL** on **Azure Virtual Machines**
* Configure **MySQL users and databases**
* Perform **basic CRUD operations**
* Install MySQL on **Ubuntu Linux** and **Windows**
* Prepare Azure **NSG for MySQL access (Port 3306)**

---

## 2️⃣ Azure Prerequisites

### Azure VM

* Ubuntu Linux VM **or** Windows VM
* Public IP attached (for labs)
* SSH (Linux) or RDP (Windows) access

### Network Security Group (NSG)

Add **Inbound Rule**:

| Setting  | Value              |
| -------- | ------------------ |
| Port     | **3306**           |
| Protocol | TCP                |
| Source   | Your IP / Internet |
| Action   | Allow              |

---

## 3️⃣ MySQL Installation on Azure VM – Ubuntu Linux

### Step 1: Update Packages

```bash
sudo apt update -y
```

### Step 2: Install MySQL Server

```bash
sudo apt install mysql-server -y
```

### Step 3: Verify Installation

```bash
mysql --version
```

### Step 4: Start & Enable MySQL Service

```bash
sudo systemctl start mysql
sudo systemctl enable mysql
```

### Step 5: Login as Root

```bash
sudo mysql
```

---

## 4️⃣ MySQL User & Database Configuration

### Create MySQL User

```sql
CREATE USER 'atul'@'localhost' IDENTIFIED BY 'Pass@123';
```

### Grant Privileges

```sql
GRANT ALL PRIVILEGES ON university.* TO 'atul'@'localhost';
```

### Fix Authentication Plugin (Recommended)

```sql
ALTER USER 'atul'@'localhost'
IDENTIFIED WITH mysql_native_password
BY 'StrongPassword@123';
```

### Apply Changes & Exit

```sql
FLUSH PRIVILEGES;
EXIT;
```

### Login with New User

```bash
mysql -u atul -p
```

---

## 5️⃣ Database Operations (University Database)

### Show Databases

```sql
SHOW DATABASES;
```

### Create Database

```sql
CREATE DATABASE university;
```

### Use Database

```sql
USE university;
```

### Show Tables

```sql
SHOW TABLES;
```

### Create Table

```sql
CREATE TABLE Course (
  CourseID INT,
  CourseName VARCHAR(1000),
  Rating NUMERIC(2,1)
);
```

### Insert Records

```sql
INSERT INTO Course VALUES
(1,'AZ-204 Developing Azure Solutions',4.5),
(2,'AZ-303 Architecting Azure Solutions',4.6),
(3,'DP-203 Azure Data Engineer',4.7);
```

### Read Data

```sql
SELECT * FROM Course;
```

---

## 6️⃣ MySQL Installation on Azure VM – Windows

### Step 1: Open PowerShell as Administrator

### Step 2: Install Chocolatey

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force;
[System.Net.ServicePointManager]::SecurityProtocol =
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072;
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### Step 3: Install MySQL Using Chocolatey

```powershell
choco install mysql -y
```

### Step 4: Verify Installation

```powershell
mysql --version
```

📌 Alternatively:

* Download **MySQL Community Server**
* Install via GUI
* Configure root password and Windows service

---

## 7️⃣ MySQL Client Usage on Linux

### Install MySQL Client

```bash
sudo apt install mysql-client -y
```

### Start MySQL Service

```bash
sudo systemctl start mysql
sudo systemctl enable mysql
```

### Login to MySQL

```bash
sudo -u root mysql
```

---

## 8️⃣ Basic CRUD Operations (Practice)

### Create Database

```sql
CREATE DATABASE mydatabase;
USE mydatabase;
```

### Create Table

```sql
CREATE TABLE mytable (
  id INT,
  name VARCHAR(100)
);
```

### Insert Records

```sql
INSERT INTO mytable VALUES (1,'Azure'), (2,'DevOps');
```

### Read Records

```sql
SELECT * FROM mytable;
```

---

## 9️⃣ Common Issues & Fix

### ❌ Access Denied Error

```text
ERROR 1045 (28000): Access denied for user
```

✅ Fix:

```sql
ALTER USER 'user'@'localhost'
IDENTIFIED WITH mysql_native_password
BY 'password';
FLUSH PRIVILEGES;
```

---

## 🔐 Best Practices

* Do **not** expose port 3306 publicly in production
* Use **private IP / VNet peering**
* Strong passwords
* Grant **least privilege**
* Regular backups

---

## ✅ Summary

✔ Installed MySQL on Azure VM (Ubuntu & Windows)
✔ Configured users, databases, and permissions
✔ Performed CRUD operations
✔ Ready for Azure cloud labs and demos

---
