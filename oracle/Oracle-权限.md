# Oracle 权限
### Oracle 权限分类
* 系统权限
* 普通对象权限
## 系统权限
### 获得系统权限信息
* 查询某一用户拥有的所有权限 (dba_sys_privs)
    SELECT * FROM dba_sys_privs where lower(grantee) = 用户名
* 查询Oracle中所有的系统权限(system_privilege_map)
    SELECT * FROM system_privilege_map

### 分配系统权限
> 在新创建一个用户后，其不具备任何权限，因此一定要给予其一定的权限。

*新用户需要与数据库建立会话*：grant create session to 用户名
*赋予创建数据表的权限*： grant create table to 用户名
*为用户分配表空间可用的空间* alter user 用户名 quota 100m on users

### 回收系统权限
> 如果某个用户拥有不需要的权限后，可以将其回收

*回收与数据库建立会话的权限*: revoke create session from 用户名
*回收创建数据表的权限*： revoke create table from 用户名

### 将已经分配的系统权限分配给其他用户（admin option）
> 如果某个用户被分配一个权限后，可以通过admin option将其分配给其它用户

有两个用户 user1与user2,如果想将user1的create session 赋予 user2,则
需要：grant create session to user1 with admin option
    登陆user1,grant creat session to user2

## 对象权限(dba_tab_privs)
对象权限指已经存在对象上的权限（当一个用户被赋予创建表的权限后默认拥有），
主要有以下几种：select,insert,update,delete,execute,
index,references,alter等

### 分配对象权限
> 如果想将当前用户的对象权限分配给其它用户，则需要进行对象权限分配
格式 ：grant 权限 on 对象 to 用户

*分配select查询权限给其它用户* grant select on 对象名 to 用户名
*分配inset权限给其它用户* grant insert on 对象名 to 用户名

### 回收对象权限
> 回收特定用户对本对象的权限，则需要进行对象权限的回收
格式：revoke 权限 on 对象 from 用户

### 将已经分配的对象权限分配给其它用户（grant option）
> 在分配权限的时候通过指定 with grant option来赋予该用户有把权限分配给
其它用户的权利