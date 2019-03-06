apt-get install supervisor

supervisorctl -c /etc/supervisord.conf

supervisorctl status

supervisorctl stop|start|restart   process_name|all