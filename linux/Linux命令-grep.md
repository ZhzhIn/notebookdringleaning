xxx$	以xxx结尾

-i	一起输出

--line-buffered	实时刷新

grep -v 显示不匹配的行

grep -i 不区分大小写

grep -l 只列出匹配文件名

grep -L 列出不匹配的文件名

grep -w 只匹配整个单词

grep -A number key filename 匹配关键词的后面分别显示number行
grep -B number key filename 匹配关键词的前面分别显示number行
grep -C number key filename 匹配关键词的上下分别显示number行 和grep -number key filename 效果相同
grep -o -i +文件名 只匹配关键词

grep -r -I -w “关键词” +目录 在当前目录下递归搜索关键词在哪个文件夹

grep “key” +文件名 | grep “key2”….同时匹配多个关键词 grep “123” 1.txt|grep “456”

grep 同时满足多个关键字和满足任意关键字

① grep -E “word1|word2|word3” file.txt
满足任意条件（word1、word2和word3之一）将匹配。

② grep word1 file.txt | grep word2 |grep word3
必须同时满足三个条件（word1、word2和word3）才匹配。

grep -E “key1|key2” 两个grep条件or关系 grep -E “vv|aabb” 3/1.txt

egrep “^linux” +文件名 搜索以linux开头的

egrep “3$” +文件名 搜索以3结尾的

在筛选条件后加–color 关键词颜色会高亮显示

查找s开头的行：grep ^s e.txt

查找n开头的行：grep n$ e.txt

grep后跟正则是需要加-E；加E是扩展的 不加E是原生的;如果正则表达式涵\d，则需要把-E改成-P，例如：grep -P “\d[1-3]\w*.” e.txt