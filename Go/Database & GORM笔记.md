# Database & GORM学习笔记

[PPT](https://bytedance.larkoffice.com/file/boxcngmUNHi2joONiiEOgSpJt8d)
[数据库与sql基本概念](https://zhuanlan.zhihu.com/p/41576768)
[用 database/sql 建立连接并使用](https://github.com/go-sql-driver/mysql)
[DSN解读](https://en.wikipedia.org/wiki/Data_source_name)
[GORM解析](https://gorm.io/docs/index.html)

目录
[Database & SQL](#1)


[GORM简介](#2)


[GORM设计原理](#3)


[GORM实践](#4)



## <span id="1">Database & SQL</span>
Database/Sql设计原理：
**应用程序**通过`操作接口`连接**database/sql**，**database/sql**通过`连接接口`和`操作接口`与**数据库**进行交互

DB连接的几种类型
+ 直接连接/Conn
+ 预编译/Stmt
+ 事务/Tx

处理返回数据的几种方式
+ Exec/ExecContext->Result
+ Query/QueryContext->Rows(Columns)
+ QueryRow/QueryRowContext->Row(Rows简化)

## <span id="2">GORM简介</span>
设计简洁、功能强大、自由扩展的全功能ORM

设计原则：API精简、测试优先、最小惊讶、灵活扩展、无依赖、可信赖
功能完善：
+ 关联：一对一、一对多、单表自关联、多态；Preload、Joins预加载、级联删除；关联模式；自定义关联表
+ 事务：事务代码块、嵌套事务、Save Point
+ 多数据库、读写分离、命名参数、Map、子查询、分组条件、代码共享、SQL表达式(查询、创建、更新)、自动选字段、查询优化器
+ 字段权限、软删除、批量数据处理、Prepared Stmt、自定义类型、命名策略、虚拟字段、自动track时间、SQL Builder、Logger
+ 代码生成、复合主键、Constraint、Prometheus、Auto Migration、真·跨数据库兼容...
+ 多模式灵活自由扩展
+ Developer Friendly

模型定义
```go
type User struct {
    ID uint
    Name string
    Email *string
    Age uint8
    Birthday *time.Time
    MemberNumber sqlNullString
    ActivatedAt sql.NullTime
    CreatedAt time.Time
    UpdatedAt time.Time
    DeletedAt gorm.DeletedAt `gorm:"index"`
}
```

约定优于配置
+ 表名为struct name的snake_cases复数格式
+ 字段名为field name的snake_case单数格式
+ ID/Id字段为主键，如果为数字，则为自增主键
+ CreatedAt字段，创建时，保存当前时间
+ UpdatedAt字段，创建、更新时，保存当前时间
+ gorm.DeletedAt字段，默认开启soft delete模式

一切都可配置，[参考链接](https://gorm.io/docs/conventions.html)

## <span id="3">GORM设计原理</span>
学的有点懵逼

























## <span id="4">GORM实践</span>































