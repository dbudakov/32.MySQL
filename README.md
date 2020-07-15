Для проверки после деплоя стенда, по выполнению команды `vagrant up` из директории `./homework`, нужно произвести записть в базу `bet`, таблицу `bookmaker`, выполнив следующую команду на `master'e`, в результате появися запись под id `1`, со значением `1xbet`

```
master> sudo mysql -e "INSERT INTO bet.bookmaker (id,bookmaker_name) VALUES(1,'1xbet');"
```

Проверить что запись реплицировалась нужно с сервера `slave`, выполнив

```
slave> sudo mysql -e "SELECT \* FROM bet.bookmaker;"
```

Проверить что репликация идет с использованием `GTID`, можно проверив включен ли этот мод на двух серверах

```
sudo mysql -e "SHOW VARIABLES LIKE 'gtid_mode';"
```
