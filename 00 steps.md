```
https://github.com/atulkamble/WebAppDB

sudo apt update -y
sudo apt upgrade -y
sudo apt install mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql

sudo mysql -u root

SHOW DATABASES;

CREATE DATABASE university;

USE university;

SHOW DATABASES;

CREATE TABLE Course(CourseID int, CourseName varchar(1000),  Rating numeric(2,1));

INSERT INTO Course(CourseID,CourseName,Rating) VALUES(1,'AZ-204 Developing Azure solutions',4.5);
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(2,'AZ-303 Architecting Azure solutions',4.6); 
INSERT INTO Course(CourseID,CourseName,Rating) VALUES(3,'DP-203 Azure Data Engineer',4.7);

SELECT * FROM Course;
```
