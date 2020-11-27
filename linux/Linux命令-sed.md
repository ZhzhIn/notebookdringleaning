正则表达式

	^开头$结尾

	[a-z][0-9]区间，如果开头带有^表示不能匹配区间内的元素

	* 0个或多个

	.表示任意字符
	
多行合并单行

如果未指定行号，则是在每一行前或后处理

i是插入所以是在每行前面 a是追加所以是在每行后面

a:新增 sed -e ‘5 a string111’ filename #在文件第5行后新增 sed -e ‘3,5 a string111’ filename #在文件第3-5行后新增

c:取代 sed -e ‘3 c str1’ filename #将文件第3行取代为str1 sed -e ‘3,5 c str1’ filename #将文件第3-5行取代为str1

d:删除 sed -e ‘2 d’ filenam #将文件第二行删除 sed -e ‘2,5 d’ filename # 将文件第2-5行删除

i:插入 sed -e ‘2 i str111’ filename #在文件第2行出插入str111 #范围插入同上

p:打印

sed -n ‘/root/p’ filename #打印含有关键词root的行

sed -n ‘/root/!p’ filename #打印不含有关键词root的行

sed -n ‘/^!/p’ filename #打印以！开头的行

sed -n ‘/t$/p’ filename #打印以字母t结尾的行

s:替换 sed -e ‘s/old/new/g’ filename # 全局替换将文件内old替换为new

s:替换 sed -e ‘s/old/new’ filename # 将文件内第一个old替换为new

i:修改源文件 将上面的-e修改为-i处理时将会修改源文件（慎用）