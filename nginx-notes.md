# Nginx Basic Command Notes 
# Nginx 基本命令笔记

---

## Table of Contents  

1. Stop and Restart Nginx Container / 停止并重启 Nginx 容器  
2. Run Nginx with Mounted Config and HTML Directory / 启动 Nginx 容器（带挂载配置与页面目录）  
3. Future Expansion (Proxy, SSL, Logging, etc.) / 后续扩展（反向代理、SSL、日志配置等） 

---

## 1️⃣ Stop and Remove Nginx Container (for Restart) 

```bash
docker stop my-nginx
docker rm my-nginx
```

## 2️⃣ Run Nginx Container with Mounted Config and Static HTML
## 2️⃣ 启动 Nginx 容器（带配置文件和静态网页目录挂载）

```bash
docker run -d \
  --name my-nginx \
  -p 80:80 \
  -v ~/my-nginx/default.conf:/etc/nginx/conf.d/default.conf \
  -v ~/my-project/html:/usr/share/nginx/html \
  registry.cn-hangzhou.aliyuncs.com/zhengqing/nginx
```
### Parameter Explanation / 参数说明：

-p 80:80
    Map local port 80 to container port 80 / 映射本地端口 80 到容器端口 80

-v default.conf:/etc/nginx/conf.d/default.conf
    Mount your custom Nginx config file / 挂载自定义 Nginx 配置文件

-v html:/usr/share/nginx/html
    Mount static website folder to Nginx web root / 挂载自定义静态网页目录

registry.cn-hangzhou.aliyuncs.com/zhengqing/nginx
    Docker image used / 使用的镜像地址

## 3️⃣ Future Expansion (To Be Continued)

Reverse Proxy Setup / 反向代理配置

SSL Certificate (HTTPS) / SSL证书配置

Nginx Access & Error Logs / 日志路径说明

Reloading Config without Restarting / 无需重启热更新配置

Use with Frontend Frameworks / 搭配前端项目部署（Vue、React 等）

---

_Last updated: June 12, 2025_  
_Compiled by: Riley_

