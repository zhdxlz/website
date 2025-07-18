# Nginx WebDAV Share

## 项目简介
本项目基于Nginx+WebDAV，适合在Android（如Termux）环境下搭建极简“多人发帖共享”平台，支持图片、视频、文字等文件的上传与浏览。

## 安装步骤（以Termux为例）

1. 安装Nginx
   ```sh
   pkg install nginx-extras
   ```

2. 创建项目目录
   ```sh
   mkdir -p ~/nginx-webdav-share/share
   mkdir -p ~/nginx-webdav-share/www
   cd ~/nginx-webdav-share
   ```

3. 将 `nginx.conf` 复制到 `~/nginx-webdav-share/` 目录下。

4. 启动Nginx
   ```sh
   nginx -c ~/nginx-webdav-share/nginx.conf
   ```

5. 用浏览器访问 http://<你的安卓IP>:8080/ 进行发帖和浏览。

6. 用WebDAV客户端（如ES文件浏览器、Solid Explorer）连接：
   ```
   http://<你的安卓IP>:8080/share/
   ```
   上传图片/视频/文本即为“发帖”，所有人可浏览和下载。

## 可选：开启账号密码认证
1. 安装htpasswd工具
   ```sh
   pkg install apache2-utils
   ```
2. 创建密码文件
   ```sh
   htpasswd -c ~/nginx-webdav-share/.htpasswd 用户名
   ```
3. 取消nginx.conf中相关注释，重启Nginx。

## 注意事项
- 所有内容均存储在 `share/` 目录下，注意备份。
- 适合局域网内使用，公网请注意安全。
