# 游标和连接属性查看器

翻译：xinjie  2019.06.30

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
xx.Set(ALIAS()) && show properties for current alias (string)
xx.Set(SELE()) && show properties for current alias (number)
xx.Set(0) && show properties for zero alias
```

连接属性：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.Set(1) && show properties for connection with handle 1
xx.Set(0) && show properties for zero connection 
```

运行模式对话框：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.Show=1 && modal dialog (2 is modeless)
xx.Set(0) && show properties for zero connection 
```

运行顶层表单对话框：
```foxpro
SET CLASSLIB TO proper.vcx ADDITIVE
xx=CREATEOBJECT("_prop_connect")
xx.AsTopLevel=.T.
xx.Set(0) && show properties for zero connection 
```

## 3) Zero connection and zero cursor
VFP can set properties for default cursor and connection - 0 (zero).
 VFP use these properties for new connections and cursors created by local view, remote view, `SQLEXEC()` and CursorAdapter.


## 4) Example
 The exmaple is in folder example, file test.prg.
 The file contain sample for openned table, local view, remote view a cursor created by CursorAdapter.


## 5) File list
proper.vcx,proper.vct - Visual library with needed class definition
cur_prop.h - Header file with needed any constants for internaly using
readme.md - Read me


folder example:
 XXD000.DBC,XXD000.DCT,XXD000.DCX - VFP database contain a link to DBF, connection to MDB, one local and remote view
 XXD000.MDB - Any MDB file with one table
 XXT000.DBF - Table linked to XXD001.DBC
 test.prg - Source code


## 6) Problems
This library is compiled under VFP 7.0. For other version is needly recompile before using.


