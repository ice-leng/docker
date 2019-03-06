

# 安装 
apt-get install supervisor

# 配置文件目录
/etc/supervisor/conf.d

# 使用
supervisorctl -c /etc/supervisord.conf

supervisorctl status

supervisorctl stop|start|restart   process_name|all