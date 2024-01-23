# WebAppDB
WebApp on Azure &amp; Database Connectivity

You can use the following resources as a reference for the Azure Web App and Virtual Network Integration
The following can be used as a reference
0) Create & Launch instance | Connect 
```
sudo apt update -y 
sudo -i passwd
sudo apt install mysql-server -y
mysql -u root -p
```
1) First go ahead and download the MySQL server community edition on the server.
https://dev.mysql.com/downloads/windows/installer/8.0.html
2) The following commands can be executed in MySQL Workbench for the creation of the database, table and adding of data
a) Create the database
```ruby
create database appdb;
```
b) Change to the context to the database
```ruby
use appdb;
```
c) Create a table
```ruby
CREATE TABLE Course
(CourseID int, CourseName varchar(1000),  Rating numeric(2,1));
```
d) Insert records into the table
```ruby
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(1,'AZ-204 Developing Azure solutions',4.5);
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(2,'AZ-303 Architecting Azure solutions',4.6); 
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(3,'DP-203 Azure Data Engineer',4.7);
```
g) See the data in the table
```ruby
SELECT * FROM Course;
```
# Basic Database Practice
mysql> ``` SHOW DATABASES;```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
6 rows in set (0.00 sec)


mysql> ``` CREATE DATABASE university;```
Query OK, 1 row affected (0.03 sec)

mysql> ``` SHOW DATABASES;```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| university         |
| world              |
+--------------------+
7 rows in set (0.00 sec)

mysql> ```USE university;```
Database changed
mysql> SHOW TABLES;
Empty set (0.01 sec)

mysql> ```CREATE TABLE students;```
ERROR 4028 (HY000): A table must have at least one visible column.
mysql> CREATE TABLE student (StudentID int, StudentName char(20));
Query OK, 0 rows affected (0.07 sec)

mysql> ```SHOW TABLES;```
+----------------------+
| Tables_in_university |
+----------------------+
| student              |
+----------------------+
1 row in set (0.00 sec)

mysql> ```SELECT * FROM student;```
Empty set (0.00 sec)

mysql> ```INSERT INTO student(StudentID, StudentName) VALUES(1,'Ram');```
Query OK, 1 row affected (0.01 sec)

mysql> ```INSERT INTO student(StudentID, StudentName) VALUES(2,'Sita');```
Query OK, 1 row affected (0.01 sec)

mysql> ```SELECT * FROM student;```
+-----------+-------------+
| StudentID | StudentName |
+-----------+-------------+
|         1 | Ram         |
|         2 | Sita        |
+-----------+-------------+
2 rows in set (0.00 sec)
