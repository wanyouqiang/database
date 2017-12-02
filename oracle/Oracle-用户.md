# Oracle 用户
### Oracle用户分类
* 系统用户（SYSTEM,SYS）
    具有系统管理权限的用户，SYS的权限功能大于SYSTEM用户，SYS用户可以管理其它
    用户。
* 普通用户
### 创建普通用户
* 语法格式：
    CREATE USER 用户名 IDENTIFIED BY 用户密码
* 创建用户时指定表空间
    CREATE USER 用户名 IDENTIFIED BY 用户密码 DEFAULT TABLESPACE USERS
### 修改用户密码
* 登陆SYS用户，书写语句ALTER USER 用户名 IDENTIFIED BY 用户密码
* 忘记SYS用户密码解决方法
    打开sqlplus使用/作为用户名与密码登陆，可以个性本身的密码与其它用户密码
### 用户锁定与解除锁定
* 锁定用户
    ALTER USER 用户名 ACCOUNT LOCK；
* 解锁用户
    ALTER USER 用户名 ACCOUNT UNLOCK;
### 查询所有用户（dba_users）
* select * from dba_users;
