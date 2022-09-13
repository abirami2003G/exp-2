# exp-2
Enter password: *******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.30 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database school;
Query OK, 1 row affected (0.01 sec)

mysql> use school;
Database changed
mysql> create table dept(deptno int(3) primary key);
Query OK, 0 rows affected, 1 warning (0.03 sec)

mysql> desc dept;
+--------+------+------+-----+---------+-------+
| Field  | Type | Null | Key | Default | Extra |
+--------+------+------+-----+---------+-------+
| deptno | int  | NO   | PRI | NULL    |       |
+--------+------+------+-----+---------+-------+
1 row in set (0.03 sec)

mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3) constraint foreign key FKey2 references dept(deptno));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key FKey2 references dept(deptno))' at line 1
mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3) constraint FKey2 references dept(deptno));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'references dept(deptno))' at line 1
mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3) constraint FKey2 foreign key references dept(deptno));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key references dept(deptno))' at line 1
mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3) constraint FKey2 foreign key(deptno) references dept(deptno));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(deptno) references dept(deptno))' at line 1
mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3) foreign key(deptno) references dept(deptno));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key(deptno) references dept(deptno))' at line 1
mysql>  create table Emp(EmpNo int(5),EName varchar(15),Job char(10),DeptNo int(3),foreign key(deptno) references dept(deptno));
Query OK, 0 rows affected, 2 warnings (0.02 sec)

mysql> desc Emp;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| EmpNo  | int         | YES  |     | NULL    |       |
| EName  | varchar(15) | YES  |     | NULL    |       |
| Job    | char(10)    | YES  |     | NULL    |       |
| DeptNo | int         | YES  | MUL | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> create table student(regno int(6) check(length(regno<=4)),mark int(3) check(mark>=0 and mark<=100));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_1'.
mysql>
mysql> create table student(regno int(6),mark int(3) check(mark>=0 and mark<=100));
Query OK, 0 rows affected, 2 warnings (0.01 sec)

mysql> desc student;
+-------+------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-------+------+------+-----+---------+-------+
| regno | int  | YES  |     | NULL    |       |
| mark  | int  | YES  |     | NULL    |       |
+-------+------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table student add constrain check(length(regno<=4));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'check(length(regno<=4))' at line 1
mysql> alter table student add check(length(regno<=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check(length(regno <=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check (length (regno <=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check (length(regno<=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check(length(regno<=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check(length(regno<=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> select * from student;
Empty set (0.00 sec)

mysql> alter table student add check(length(regno<=4));
ERROR 3812 (HY000): An expression of non-boolean type specified to a check constraint 'student_chk_2'.
mysql> alter table student add check length(regno<=4);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'length(regno<=4)' at line 1
mysql> alter table student add check length(regno)<=4));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'length(regno)<=4))' at line 1
mysql> alter table student add check(length(regno)<=4));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> alter table student add check(length(regno)<=4);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> create table cust(custid int(6) not null,name varchar(10));
Query OK, 0 rows affected, 1 warning (0.01 sec)

mysql> alter table cust modify column name varchar(10);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc cust;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| custid | int         | NO   |     | NULL    |       |
| name   | varchar(10) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> create table cust(custid int(6) unique,name varchar(10));
ERROR 1050 (42S01): Table 'cust' already exists
mysql> create table cost(custid int(6) unique,name varchar(10));
Query OK, 0 rows affected, 1 warning (0.03 sec)

mysql> alter table cost add unique(custid);
Query OK, 0 rows affected, 1 warning (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 1

mysql> desc cost;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| custid | int         | YES  | UNI | NULL    |       |
| name   | varchar(10) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> create table stud(regno int(6) primary key,name varchar(20));
Query OK, 0 rows affected, 1 warning (0.01 sec)

mysql> desc stud;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| regno | int         | NO   | PRI | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql>
