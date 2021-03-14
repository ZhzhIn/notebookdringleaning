String 
1.“”是长度为0的String，null是对象不存在
2.每次连接字符串，都会构建一个新的String对象，使用StringBuilder可以避免这个问题的发生。
3.StringBuffer是StringBuilder的前身，它线程安全；