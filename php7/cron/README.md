

# 安装 
apt-get install cron

# 配置文件目录
/etc/cron.d

# 使用
```` php

* * * * * command

几个星号分别为：分 时 日 月 周，最后是要执行的命令。
    分：0~59
    时：0~23
    日：1~31
    月：1~12
    周：0～6（0表示星期天）
    
除了数字还有几个个特殊的符号就是* / - ：
    * 代表所有的取值范围内的数字
    / 代表每的意思
    */5 表示每5个单位
    - 代表从某个数字到某个数字
    , 分开几个离散的数字
    
配置文件的一些例子：
    0 3 * * * /root/test.sh 每天凌晨3点执行test.sh文件
    * 23-7/1 * * * /root/lnmp restart 晚上11点到早上7点之间，每隔一小时重启lnmp套件
    */30 * * * * /usr/sbin/ntpdate 每半小时同步一下时间
    0 23 * * 6 /lnmp restart 每星期六的11 : 00 pm重启重启lnmp套件。
    */1 * * * * echo "i am running.">>/tmp/running.txt 每隔1分钟向/tmp/running.txt写一个"i am running."字符串。    
        
   
运行
    我以为编辑crontab保存后会自动执行，其实不然，必须通过重启cron才可以，命令如下：
    启动  /etc/init.d/cron start
    关闭  /etc/init.d/cron stop
    重启  /etc/init.d/cron restart   
   
````