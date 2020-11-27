查看每一列
	awk 'NR==2{for(i+1;i<=NF;i++) print i " = "$i}'
NF 总列数
awk -F \"
	-F 按照后面的字符分割
单行拆多行
	1.sed 's#word#_'
	sed 's#><#>_<'
	2. awk  'BEGIN {RS="_"}1'
NR 读取的数据行数
awk ‘pattern+action’ [filename]
-pattern 正则表达式
-action 对匹配到的内容执行的命令（默认是输出的每行内容）
例子：
搜索/etc/passwd文件内有root关键词的所有行，并显示对应的shell
awk -F : ‘/root/{print $0}’ /etc/passwd #搜索/etc/passwd文件内有root关键词的所有行
awk -F : ‘/root/{print $7}’ /etc/passwd #搜索/etc/passwd文件内有root关键词的所有行，并显示对应的shell
打印/etc/passwd的第二行信息
awk -F : ‘NR==2{print $0}’ /etc/passwd

筛选文件内地3行至第10行信息

awk -F : ‘{if(NR>=3 && NR <=10)print $0}’ filename

awk多个分隔符— '[ ,]'空格或者逗号是分隔符，这俩碰见哪个都算数

awk -F ‘[ ,]’ ‘{print $3 " "$7}’ bwwk.txt

多个条件—筛选文件第2-3行的数据且含有2809

awk -F : ‘/2809/{if(NR>=2 && NR <=3)print $0}’ awwk.txt

给打印出来的信息加个标题

awk -F : ‘BEGIN{print “title”} {if(NR>=2 && NR <=3)print $0}’ awwk.txt

自定义分隔符

echo “111 222|333 444|555 666” |awk ‘BEGIN{RS="|"}{print $0}’

awk和grep配合使用，两个条件关系为and

awk -F : ‘{if(NR>=2 && NR <=3)print $0}’ awwk.txt | grep ‘2809’ --color

把两个文件按照对应的每行放在同一行上，可以用paste

paste filename1 filename2 #未设置分隔符默认tab键

paste -d “=” filename1 filename2 #设置分隔符为=