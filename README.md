BAI 2: KHOI CHAY WEB SERVER NGINX VOI PORT MAPPING

1. MUC TIEU
- Chay mot Nginx Web Server dang container o che do chay ngam (-d).
- Thuc hien anh xa cong mang tu host sang container (-p 8080:80).
- Kiem tra phan hoi web server va don dep container sau khi hoan thanh.

2. BOI CANH VA YEU CAU
- Image su dung: nginx:alpine (nhe, toi uu).
- Ten container: my-web.
- Port mapping: 8080 (host) : 80 (container).
- Kiem tra ket qua bang curl.

3. CAC BUOC THUC HIEN VA KET QUA TERMINAL THUC TE

3.1. Khoi chay Nginx Web Server o che do chay ngam
Lenh thuc hien:
```bash
docker run -d -p 8080:80 --name my-web nginx:alpine
```
Ket qua dau ra:
```text
c9f9f29bc31146fc8115e788a327717ab2b682a0d75307aa8669ff01e37eff8b
```

3.2. Kiem tra danh sach container dang chay
Lenh thuc hien:
```bash
docker ps
```
Ket qua dau ra:
```text
CONTAINER ID   IMAGE          COMMAND                  CREATED                  STATUS                  PORTS                                     NAMES
c9f9f29bc311   nginx:alpine   "/docker-entrypoint.…"   Less than a second ago   Up Less than a second   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web
```

3.3. Gui truy van kiem tra phan hoi Web Server
Lenh thuc hien:
```bash
curl -s http://localhost:8080
```
Ket qua dau ra:
```text
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

3.4. Dung va xoa container sau khi thu nghiem
Lenh thuc hien:
```bash
docker stop my-web && docker rm my-web
```
Ket qua dau ra:
```text
my-web
my-web
```

3.5. Xac nhan container da duoc don dep
Lenh thuc hien:
```bash
docker ps -a
```
Ket qua: Container my-web da duoc dung va xoa hoan toan khoi he thong.

4. TONG KET CAC LENH
```bash
docker run -d -p 8080:80 --name my-web nginx:alpine
docker ps
curl -s http://localhost:8080
docker stop my-web && docker rm my-web
docker ps -a
```
