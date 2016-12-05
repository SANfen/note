* [1.mysql常用命令](#1)
    * [1.1mysql修改密码](#1.1)
    * [1.2mysql开启远程连接](#1.2)

<h1 id="1">1. mysql常用命令</h1>


----------
<h2 id="1.1">1.1 mysql修改密码</h2>
#####第一种方法

    mysql -uroot -p
    Enter password: 【输入原来的密码】
    mysql>use mysql;
    mysql> update user set password=password("test") where user='root';
    mysql> flush privileges;
    mysql> exit;  

#####第二种方法

    mysql -u root
    mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpass');
    
#####第三种方法，在丢失root密码的时候，可以这样

    mysqld_safe --skip-grant-tables&
    mysql -u root mysql
    mysql> UPDATE user SET password=PASSWORD("new password") WHERE user='root';
    mysql> FLUSH PRIVILEGES;
    
----------
<h2 id="1.2">1.2 mysql开启远程连接</h2>
    
    mysql -u root
    mysql> use mysql;
    mysql> update user set host = ‘%’ where user = ‘root’;
    mysql> select host, user from user;
    mysql> flush privileges;
    /*如果需要关闭远程连接把%换成localhost就行*/
