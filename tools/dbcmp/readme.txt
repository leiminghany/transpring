说明:
dbcmp用于比较数据库的两个表之间的差异,并通过WEB的形式高亮显示。
dbcmp运行于Linux/Unix平台,目前只支持Oracle.
运行前用户要配置dbcmp.cfg、dbcmp.tbl、dbcmp.xcols文件.
运行./dbcmp命令可以查看帮助，运行dbcmp run命令执行数据比较。
比较完后系统将生成一个html的报表文件,可以通过浏览器打开。

配置文件说明：
dbcmp.tbl：参与比对数据库表配置文件。
填写要参与比对的表名，可以带WHERE条件，如果没有WHERE条件，系统将采用全局配置的default_condstr参数。
文件支持整行#注释

dbcmp.xcols：不参与比对的列配置。
表名写在最前面，然后一个:分割，最后是每个列名，列名需要用|分割，最后要以|结束。
_GLOBAL__ 表示匹配所有表的列名。
一个表的配置可以写在多行，并且支持#最整行注释。
