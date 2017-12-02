# Oracle控制结构

### 选择结构
    ·
        declcare n number(3) := 10; -- 声明一个变量并赋值
        begin
            if n > 0 then
                dbms_output.put_line('n大于0');
            elsif n = 0 then
                dbms_output.put_line('n等于0');
            else
                dbms_output.put_line('n小于0');
            end if;
        end;

    ·

### 分支结构
    `
        declare week varchar2(3) := 'MON'; -- 声明并初始化一个字符型的变量
        begin
            case week
                when 'MON' then
                    dbms_output.put_line('星期一');
                when 'TUE' then
                    dbms_output.put_line('星期二');
                when 'WED' then
                    dbms_output.put_line('星期三');
                when 'THU' then
                    dbms_output.put_line(‘星期四’);
                else dbms_output.put_line('其它');

    `


### 循环结构 (loop)
* while循环
    ·
        declare n number(3) := 0;
        begin
            while n < 10 loop
                dbms_output.put_line(n);
                n := n + 1;
            end loop;
        end;
    ·

* loop 循环
    ·
        declare n number(3) := 0;
        begin
            loop 
                if n > 10 then
                    exit;
                end if;
                dbms_output.put_line(n);
                n := n + 1;
            end loop;
        end;

    ·