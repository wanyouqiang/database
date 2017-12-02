# Oracle-游标
### 静态游标
* 显式游标

    1.声明一个显式游标：declcare cursor 游标变量 is 查询语句

    2.定义列类型的变量 列名 数据类型 / 列名 数据表名.列名%type

    3.定义行类型的变量 行变量名 数据表名%rowtype;

    4.打开游标 open 游标变量

    5.捕获数据 fetch 游标变量 into 行变量、列变量；

    6.循环读取

    7.关闭游标 close 游标变量


* 隐式游标

    1.sql隐式游标
    常用属性：isopen可判断游标是否被开启

    `begin
        if sql%isopen then
        dbms_output.put_line('游标开启');
        else
        dbms_output.put_line('游标关闭');
        end if;
    end;`

    rowcount统计更新的记录数

    `begin
           update 语句；
           dbms_output.put_line('捕获记录数：' || sql%rowcount);
    end;
    `

    2.cursor for 隐式游标

    语法格式：`
        begin
            for 游标变量 in （select 语句） loop
            游标变量.列名
        end loop;
        end;
    `

### 动态游标
> 动态游标将显示游标的SQL在定义时指定变成，把SQL语句放在游标打开时指定。

* 强类型动态游标（有返回值类型）

    1.声明一个强类型动态游标
    
    `
        declare type 游标变量 is ref cursor return 表名%rowtype;
    `

    2.打开指定的查询语句

    `
        open 游标变量 for select语句
    `
    3.捕获数据

    `
        fetch 游标变量 into 行类型/列类型变量
    `

    4.循环loop

    `
        while 游标变量%found loop
        行类型变量.列名/列类型变量
        end loop;
    `

    5.关闭游标
* 弱类型动态游标(没有返回值类型相对灵活)
    1.声明一个弱类型的动态游标

    `
        declare type 游标变量 is ref cursor;
    `

    2.打开指定的查询语句

    `
        fetch 游标变量 into 行类型/列类型变量
    `

    3.捕获数据

    `
        fetch 游标变量 into 行类型/列类型变量
    `

    4.循环loop

    `
        while 游标变量%found loop
        行类型变量.列名/列类型变量
        end loop;
    `

    5.关闭游标
