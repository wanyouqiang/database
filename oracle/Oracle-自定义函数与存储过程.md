# Oracle-自定义函数与存储过程
### 自定义函数
> Oracle里的函数可分为系统函数与自定义函数，自定义函数允许我们自己定义符合需求的函数

* 创建自定义函数格式

    `CREATE OR REPLACE FUNCTION 函数名(型参1 数据类型1) return 返回值类型 as
    begin
        begin
            return 返回值
        end;
    end 函数名；

    `
* 调用自定义函数
    
    `
    declare 变量名称 数据类型；
    begin
    变量名 ：= 函数名();
    dbms_output.put_line(变量名);
    end;
    `
* 查询自定义函数
    `
        select * from user_objects where object_name = '函数名';
        select * from user_source;
    `
### 存储过程
> 存储过程的书写格式与自定义函数类似，存储过程与自定义函数最大的区别是存储过程没有返回值。

* 定义一个存储过程

    `
        create or replace procedure 过程名(参数名 in/out 数据类型) as
        begin
            begin
            PL/SQL语句

            end;
        end 过程名;
    `
* 执行存储过程
    `
        begin
            存储过程名（参数）
        end;

        execute 存储过程名
    `
* 删除存储过程
    `
        drop procedure 存储过程名
    `
### 包
> Oracle里的包与Java里的包概念类似，Oracle包是用来组织自定义函数与存储过程，Oracle里的包定义分为 规范（specification） 主体(body)

* 创建一个包

    `
    create or replace package mypkg as
    begin
        function 函数名 return 数据类型;
        procedure 过程名;
    end mypkg;

    `

* 实现包的主体部分
    `
    create or replace package body mypkg as
    begin
        function 函数名 is
        begin
            begin
                return 返回值；
            end;
        end 函数名;
        
        procedure 过程名 as
        begin
            begin
                Plsql语句；
            end;
        end 过程名;
    end mypkg;
    `

* 调用包中的函数或存储过程

select 包名.函数名 from dual;

execute 包名.存储过程名;