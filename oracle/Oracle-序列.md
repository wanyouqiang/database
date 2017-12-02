# Oracle-序列（SEQUENCE）

> Oracle并没有像MySQL与SQLServer那样在数据表的单列上设置自增长属性，从而在不指定主键列的情况下实现自增长。Oracle通过序列对象来实现自增功能

### 创建序列
    * 在Oracle中创建序列与创建表，创建用户一样使用CREATE关键字
        ·
            CREATE SEQUENCE TEST_SEQ;
        ·
    * 在创建序列时指定初始值
        `
            CREATE SEQUENCE TEST_SEQ START WITH 1;
        `
    * 查询已经创建的序列（user_sequences）
        `
            select * from user_sequences where sequence_name = 'TEST_SEQ';
        `
### 使用序列
    * test_seq.currval 获取当前序列的值
    * test_seq.nextval 获取下一个序列的值

### 序列的属性
    * MINVALUE  序列的最小值

    * MAXVALUE 序列的最大值

    * INCREMENT BY 序列的步长

    * START WITH 序列的起始值 (在创建序列时指定)

    * CYCLE  当序列递增到最大值后循环
        * `ALTER SEQUENCE TEST_SEQ CYCLE`
        * `ALTER SEQUENCE TEST_SEQ NOCYCLE`

    * CACHE  缓存序列，从而提高效率
        * `ALTER SEQUENCE TEST_SEQ CACHE 10`
        * `ALTER SEQUENCE TEST_SEQ NOCACHE`

### 修改序列
    * 语法格式
        `alter sequence test_seq minvalue 1;`

### 删除序列
    * 语法格式
        `drop sequence test_seq;`