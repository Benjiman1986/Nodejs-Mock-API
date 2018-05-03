# Nodejs-Mock-API
用于Mock API，理论上应配合Nginx使用，Nginx配置类似以下：
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            proxy_pass http://localhost:8091;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

        location /cube/ {
            proxy_pass http://localhost:3000/;
            proxy_read_timeout 3m;
            send_timeout 3m;
            keepalive_timeout 3m;
        }
    }
    
 #APP 使用
 启动方法，node app或npm start
 使用系统服务启动方法：node nw.js,在windows服务里会生成一个node_mock_api的服务
 
