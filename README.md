nginx-php7.0-mysql  docker

使用方法：

首先安装Docker, 有条件的推荐用前两个方式，老设备用Toolbox

 - [Docker for Mac](https://docs.docker.com/docker-for-mac/)
 - [Docker for Windows](https://docs.docker.com/docker-for-windows/)
 - [Docker Toolbox](https://www.docker.com/products/docker-toolbox)

下载项目

    $ git clone 
    
配置环境变量

    $ cp .env.back  .env
 
 
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