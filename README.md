# sql-server-try

## docker

> [!TIP]
> 
> Microsoft SQL ServerをDockerで試す。  
> https://zenn.dev/hashito/articles/83d11192de6168  

### pull
```
docker pull mcr.microsoft.com/mssql/server:2022-latest

docker images
```

### run
```
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Passw0rd" -p 1433:1433 --name sql1 --hostname sql1 -d mcr.microsoft.com/mssql/server:2022-latest
```

### connect db
```
docker exec -it sql1 "bash"

/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "Passw0rd"
```

### create database, create table
```
create database hellodb;

go

use hellodb;

go

create table item(id int, item_name nvarchar(100), price int);

go
```

### insert, select
```
insert into item values (1, (N'ペン'), 100);

go

select * from item;

go
```

> [!TIP]
>
> SQLServerに日本語データをInsertすると文字化けする。  
> https://kitigai.hatenablog.com/entry/2018/05/27/010440  

### quit from db
```
quit
```

### exit from docker
```
exit
```

## SSMS (SQL Server Management Studio)

### download and install
SSMS-Setup-ENU.exe

### connect
```
Database Engine
localhost
SQL Server Authentication
sa
Passw0rd
```

## for install

![](image/1.PNG)
![](image/2.PNG)
![](image/3.PNG)
![](image/4.PNG)
![](image/5.PNG)
![](image/6.PNG)
![](image/7.PNG)
![](image/8.PNG)
![](image/9.PNG)
![](image/10.PNG)
![](image/11.PNG)
![](image/12.PNG)
![](image/13.PNG)
![](image/14.PNG)
![](image/15.PNG)
![](image/16.PNG)
![](image/17.PNG)
![](image/18.PNG)
![](image/19.PNG)
![](image/20.PNG)
![](image/21.PNG)


## for spring-boot

TCP/IPの有効化  
https://intellectual-curiosity.tokyo/2021/12/31/spring-boot%E3%81%A7%E3%83%87%E3%83%BC%E3%82%BF%E3%83%99%E3%83%BC%E3%82%B9%EF%BC%88sql-server%EF%BC%89%E3%81%AB%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95/  

db_owner権限付与  

application.properties
```
spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=somedb;encrypt=false
spring.datasource.username=someuser
spring.datasource.password=password
```

データファイル移動  
https://sql55.com/column/how-to-move-database-using-detach-and-attach.php  
