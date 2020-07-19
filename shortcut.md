Установка и запуск mysql
```
rpm -Uvh http://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
yum install mysql-server -y
systemctl enable mysqld && systemctl start mysqld
```

Установка, запуск и запись пароля от кластера mysql в `~/.my.cnf` для входа в `mysql` по команде `root> mysql`  
```
yum install https://repo.percona.com/yum/percona-release-latest.noarch.rpm -y
yum install  Percona-Server-server-57  -y
systemctl enable mysqld && systemctl start mysqld
grep -i root@localhost /var/log/mysqld.log |awk '{print $NF}'
echo [client] > /root/.my.cnf
echo "password=`grep -i root@localhost /var/log/mysqld.log |awk '{print $NF}'`" >> /root/.my.cnf
```
  
посмотреть пользователей:  
```  SELECT USER from mysql. user;```  
    
Создание базы  
  ```CREATE DATABASE productsdb;```    
  
Переход в базу  
  ```USE productsdb;```  
  
Создание таблицы(для таблицы требуется описание)
 ```
CREATE TABLE Customers
(
  Id INT,
  Age INT,
  FirstName VARCHAR(20),
  LastName VARCHAR(20)
);
```  
Вставка в таблицу  
```
insert into table_name values(id_number,'string_name');
```
Вывести описание таблицы
```
# https://tableplus.com/blog/2018/11/mysql-describe-explain-details-table-structure-query.html
SHOW COLUMNS FROM table_name;
DESCRIBE table_name;
DESC table_name;
EXPLAIN table_name;
EXPLAIN SELECT * FROM table_name;
```
Сортировка вывода  
```
# https://metanit.com/sql/mysql/4.3.php  
```
