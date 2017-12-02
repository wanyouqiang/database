# Oracle 角色

## 角色分类
> dba_roles 视图中保存了所有的系统角色与用户角色

### Oracle内置角色
*    *DBA*：数据库管理员角色，利用该角色可以对数据库进行所有的操作
*    *CONNECT*：该角色拥有CREATE SESSION,CREATE TABLE, CREATE VIEW
        等权限，而且这些权限不能被分配给其它用户  。
*    *RESOURCE* 可以通过查询dba_sys_privs来获取该角色拥有的权限信息
     **该权限还有一个隐含的权限---unlimited tablespace(没有表空间的限制)**

## 自定义角色

### 创建角色 (视图 dba_roles)
    语法格式：CREATE ROLE 角色名称

### 为角色分配权限(可以分配系统权限与对象权限)
    * 系统权限  grant crate session to 角色名
    * 对象权限 grant select ,update on 对象名 to 角色名

## 角色继承
    grant 父亲角色 to 孩子角色

## 禁用、启用角色
    
