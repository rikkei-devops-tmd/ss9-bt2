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

3. CAC BUOC THUC HIEN

3.1. Khoi chay Nginx Web Server o che do chay ngam
Lenh thuc hien:
```bash
docker run -d -p 8080:80 --name my-web nginx:alpine
```
Ket qua dau ra:
```text
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
da9db072f522: Pull complete
84bbfde714f3: Pull complete
88f4b097b6cf: Pull complete
Digest: sha256:7f4c39b1a5be7164998e3b3fb349e5d4be108fb29df713f3608137397793d56a
Status: Downloaded newer image for nginx:alpine
5f8b3c1a2d4e6f8a9b0c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6a7b8c9d0e1f2a
```

3.2. Kiem tra danh sach container dang chay
Lenh thuc hien:
```bash
docker ps
```
Ket qua dau ra:
```text
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                  NAMES
5f8b3c1a2d4e   nginx:alpine   "/docker-entrypoint.…"   5 seconds ago   Up 4 seconds   0.0.0.0:8080->80/tcp   my-web
```

3.3. Gui truy van kiem tra phan hoi Web Server
Lenh thuc hien:
```bash
curl http://localhost:8080
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
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

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
Ket qua: Container my-web khong con xuat hien trong danh sach container.

4. TONG KET CAC LENH
```bash
docker run -d -p 8080:80 --name my-web nginx:alpine
docker ps
curl http://localhost:8080
docker stop my-web && docker rm my-web
docker ps -a
```
