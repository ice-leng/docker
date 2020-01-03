nginx-php7.0-mysql  docker

使用方法：

首先安装Docker, 有条件的推荐用前两个方式，老设备用Toolbox,对号入座

 - [Docker for Mac](https://docs.docker.com/docker-for-mac/)
 - [Docker for Windows](https://docs.docker.com/docker-for-windows/)
 - [Docker Toolbox](https://www.docker.com/products/docker-toolbox)
 - [Docker for Linux](https://docs.docker.com/install/linux/docker-ce/centos/)
 - [Docker-compose](https://github.com/docker/compose/releases)
 - [Letsencrypt 教程](https://www.jianshu.com/p/ddc618d42cba)

下载项目

    $ git clone 
    
配置环境变量
 
    $ cp .env.back  .env
 
 
修改代理，对于使用 systemd 的系统，请在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）

     {
        "registry-mirrors": [
          "https://docker.mirrors.ustc.edu.cn"
        ]
      }
      
重启服务

    $ sudo systemctl daemon-reload
    $ sudo systemctl restart docker      
  
 
启用+build

    $ docker-compose up -d
    
重新build

    $ docker-compose down
    
服务命令

    $ docker-compose start | stop | restart 
	
进入容器

	$ docker exec -it nginx bash  
	
然后打开浏览器，就可以在http://localhost 访问到项目, 通过http://localhost:8080 访问phpmyadmin

安装额外的PHP扩展可修改php/Dockerfile，然后再重新build

注意：PDO 数据库连接

    //localhost 是mysql容器名字
    $ mysql:host=localhost;dbname=project 
    
ssl 选择的是 letsencrypt ，需要自行配置 [教程](https://www.jianshu.com/p/c5c9d071e395)

    // 进入容器 
    $ docker exec -it docker_nginx_1 bash 
    // 安装Certbot客户端 
    $ apt-get update && apt-get install certbot  &&  apt-get install cron
    
    // 获取证书 
    // 泛指
    $ certbot certonly -d *.amsimple.com --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/directory --config-dir=/xxx

    // 配置情况 nginx/vhosts/ssl.conf.back
    
    //certbot renew --config-dir=/app/docker/nginx/ssl/ --dry-run
    
    // 脚本更新
    $ crontab -e
    $ 15 2 * */2 * /usr/bin/certbot renew --config-dir=/xxx  >> /var/log/le-renew.log
    
    $ crontab    certbot-auto-renew-cron
    
    
    
