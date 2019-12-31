

# 安装 
apt-get install supervisor

# 配置文件目录
/etc/supervisor/conf.d

# 使用 [解决方案](https://blog.csdn.net/kkevinyang/article/details/80539940)
supervisord -c /etc/supervisor/supervisord.conf

supervisorctl status

supervisorctl stop|start|restart   process_name|all