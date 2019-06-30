# 游标和连接属性查看器

翻译：xinjie    2019.06.30

**本类库用于显示和设置游标和连接的属性。**

**Bugs: **
- 修复 VFP9 下的所有错误

**New:**
- 支持顶层表单

1) 对话框描述
2) 使用方法
3) 连接和游标的默认设置
4) 示例
5) 文件列表
6) 已知问题

## 1) 对话框描述
按钮“刷新”重新加载值。
按钮“选项”调用表单，用于设置自动刷新间隔（ms）。 如果value为0，则不调用autorefresh。
按钮“设置属性”保存更改的值。
按钮“确定”关闭表单。

具有灰色背景色的控件所对应的属性是只读的。
具有绿色背景颜色的控件对应的属性是可以作为连接和游标的默认设置。


## 2) 使用方法
游标属性：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_cursor")
xx.Set(ALIAS()) && 显示当前游标的属性 (字符串)
xx.Set(SELE()) && 显示当前游标的属性 (数值)
xx.Set(0) && 显示所有游标的默认属性
```

连接属性：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.Set(1) && 显示连接句柄为 1 的连接属性
xx.Set(0) && 显示连接的默认属性 
```

运行模式对话框：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.Show=1 && 模式表单
xx.Set(0) && 显示连接的默认属性 
```

运行顶层表单对话框：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.AsTopLevel=.T.
xx.Set(0) && 显示连接的默认属性 
```

## 3) 连接和游标的默认设置
VFP 可以设置游标和连接的属性默认值 - 0 。

 VFP将这些属性用于由本地视图，远程视图，`SQLEXEC（）和 CursorAdapter 创建的新连接和游标。


## 4) 示例
 示例文件可以通过执行 example 目录下的 test.prg 进行查看。
 
 示例文件包含打开表、本地视图、远程视图和 CursorAdapter 的应用。


## 5) 文件列表
proper.vcx,proper.vct - 必需的可是类库

cur_prop.h - 可视类库使用的头文件

readme.md - 本文件


目录 example:

 XXD000.DBC,XXD000.DCT,XXD000.DCX - VFP数据库，包含DBF的链接，与MDB的连接，一个本地和和一个远程视图
 
 XXD000.MDB - MDB 文件
 
 XXT000.DBF - 数据库表
 
 test.prg - 测试程序


## 6) 已知问题
该库是在VFP 7.0下编译的。 其他版本在使用前需要重新编译。

