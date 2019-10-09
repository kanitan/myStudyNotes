**环境说明**

```
Linux version 5.2.0-kali2
```

# apache环境

## 开启apache

kali自带apache2

1.配置监听端口。默认是80，一般改成8080（该步骤可省略）

```shell
vi /etc/apache2/ports.conf
```

摁下``i``编辑。修改为8080

![portChange](/Users/reyiko/Documents/notes/sqli-labs环境搭建/img/portChange.png)

```shell
：wq
sudo service apache2 start
```

2.访问``http://localhost:8080``，出现如下页面则访问

![apacheHome](/Users/reyiko/Documents/notes/sqli-labs环境搭建/img/apacheHome.png)



## 开启mysql

```shell
sudo service mysql start
```



安装完毕，接下来搞sqli-labs

# 下载项目

```
wget 
```





