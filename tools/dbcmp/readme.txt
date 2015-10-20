说明:
dbcmp用于比较数据库的两个表数据之间的差异,并通过WEB的形式高亮显示。
dbcmp运行于Linux/Unix平台,目前只支持Oracle.
运行前用户要配置dbcmp.cfg、dbcmp.tbl、dbcmp.xcols文件.
运行./dbcmp命令可以查看帮助，运行dbcmp run命令执行数据比较。
比较完后系统将生成一个html的报表文件,可以通过浏览器打开。

配置文件说明：
dbcmp.cfg：全局配置，说明如下：
db_user=scott      #数据库用户名
db_passwd=tiger      #数据库用户密码
db_inst=orcl          #数据库连接描述符
default_condstr="WHERE BANK=6320";      #要抽取数据的默认条件
prefix1=tbl_        #表1前缀
prefix2=bak_        #表2前缀
suffix1=        #表1后缀
suffix2=        #表2后缀
tablist="dbcmp.tbl"        #参与比对的表配置文件名
rptfile="report.html"         #生成的差异报告文件名
xcols_path=./           #排除列配置文件目录
xcols_file="dbcmp.xcols"        #排除列配置文件
maxrownum=500		#输出记录的最大条数
sqlvarlist=""		#声明在tablist中使用的SQL变量，用分号隔开。

dbcmp.tbl：参与比对数据库表配置文件。
填写要参与比对的表名，可以带WHERE条件，如果没有WHERE条件，系统将采用全局配置的default_condstr参数。
文件支持整行#注释
支持对一个表按照不同的where条件分组来比较，在表名后加上/*来区分，*可以是任意的字符串。

dbcmp.xcols：删除或修改参与比对的列配置。
表名写在最前面，然后一个:分割，最后是每个要删除的列名，列名需要用|分割，最后要以|结束。
_GLOBAL__ 表示匹配所有表的列名。
一个表的配置可以写在多行，并且支持#最整行注释。
两个表的差集列系统会自动删除，无需在本列中配置。
如果需要对某列在比较前使用函数处理而不是直接删除，只需要在此列后紧跟着添加|UPDATE;<expression>;|语句即可，其中<expression>是替代本列的SQL表达式。

Windows平台使用方法：
1）下载并安装git for windows。
2）安装完后打开Git Bash，之后运行如下命令下载dbcmp：
$ git clone http://code.google.com/p/transpring
3）下载完后，进入transpring/tools/dbcmp目录即可使用。

