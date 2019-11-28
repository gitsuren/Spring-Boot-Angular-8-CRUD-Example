# Angular8-SpringBoot-CRUD-Tutorial
Develop a single page application(SPA) using Angular 8 as a front-end and Spring boot restful API as a backend.https://medium.com/@mehulkothari05/spring-boot-angular-8-crud-example-8aeafd47b54

# LOCAL SET UP WITH DOCKER CONTAINER FOR MYSQL

1. Run the docker container as:
``` console
suru ~ $docker run -d  -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=users_database -p 3306:3306 mysql:5.7

5a8e3ff05f0313f9751882df3453b1a2d465868b8654f9e7f4e5c5a02377165d
suru ~ $ docker exec -it 5a8 mysql -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.28 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| users_database     |
+--------------------+
5 rows in set (0.01 sec)

mysql> use users_database;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables
    -> ;
+--------------------------+
| Tables_in_users_database |
+--------------------------+
| employees                |
| hibernate_sequence       |
+--------------------------+
2 rows in set (0.00 sec)

mysql> select * from employees;
Empty set (0.00 sec)

mysql> select * from employees;
+----+----------------+------------+-------------+
| id | email_address  | first_name | last_name   |
+----+----------------+------------+-------------+
|  1 | test@gmail.com | Surendra   | Bajracharya |
+----+----------------+------------+-------------+
1 row in set (0.00 sec)

```

2. Run the application with PROPERTIES:
```console
spring.datasource.url = jdbc:mysql://localhost:3306/users_database?useSSL=false
spring.datasource.username = root
spring.datasource.password = secret


## Hibernate Properties
# The SQL dialect makes Hibernate generate better SQL for the chosen database
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5InnoDBDialect

# Hibernate ddl auto (create, create-drop, validate, update)
spring.jpa.hibernate.ddl-auto = create
```