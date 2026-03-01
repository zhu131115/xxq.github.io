# 孝心圈官方网站

这是一个基于 HTML、CSS 的响应式官方网站，包含以下页面：

- **首页** (`index.html`) - 介绍孝心圈的核心功能和数据
- **功能概述** (`overview.html`) - 详细介绍应用的功能特性
- **下载应用** (`download.html`) - 提供应用的下载链接和安装指南
- **赞助支持** (`sponsor.html`) - 赞助方式和权益说明
- **关于我们** (`about.html`) - 团队介绍和价值观

## 部署方法

### 方法 1：使用 Nginx 托管

1. 将文件复制到 Nginx 网站目录：
```bash
mkdir -p /www/wwwroot/xiaoxinqu
cp -r /workspace/projects/official-website/* /www/wwwroot/xiaoxinqu/
```

2. 配置 Nginx：
```nginx
server {
    listen 8081;
    server_name xiaoxinqu.example.com;

    root /www/wwwroot/xiaoxinqu;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

3. 重启 Nginx：
```bash
nginx -t
nginx -s reload
```

### 方法 2：使用 Docker

1. 创建 Dockerfile：
```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
```

2. 构建并运行：
```bash
cd /workspace/projects/official-website
docker build -t xiaoxinqu-web .
docker run -d -p 8081:80 --name xiaoxinqu-web xiaoxinqu-web
```

### 方法 3：使用 Apache

1. 将文件复制到 Apache 网站目录：
```bash
mkdir -p /var/www/html/xiaoxinqu
cp -r /workspace/projects/official-website/* /var/www/html/xiaoxinqu/
```

2. 配置 Apache：
```apache
<VirtualHost *:80>
    ServerName xiaoxinqu.example.com
    DocumentRoot /var/www/html/xiaoxinqu

    <Directory /var/www/html/xiaoxinqu>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

3. 重启 Apache：
```bash
systemctl restart httpd
```

## 访问地址

部署完成后，可以通过以下地址访问：
- 本地测试：`http://localhost:8081`
- 服务器：`http://47.98.128.159:8081`

## 自定义配置

### 修改下载链接

编辑 `download.html`，修改 APK 下载链接：
```html
<a href="你的APK下载链接" class="btn btn-primary btn-large">
  下载 APK
</a>
```

### 修改联系信息

编辑所有页面，修改邮箱和电话：
```html
<li>邮箱: your-email@example.com</li>
<li>电话: 400-XXX-XXXX</li>
```

### 修改颜色主题

编辑 `css/style.css`，修改 CSS 变量：
```css
:root {
  --primary-color: #FF6B6B;  /* 主色调 */
  --secondary-color: #4ECDC4;  /* 次要色调 */
}
```

## 浏览器支持

- Chrome (推荐)
- Firefox
- Safari
- Edge
- 移动端浏览器（响应式设计）

## 特性

- ✅ 响应式设计，支持移动端和桌面端
- ✅ 现代化的 UI 设计
- ✅ 清晰的导航结构
- ✅ 完整的功能介绍
- ✅ 详细的下载指南
- ✅ 赞助支持页面
- ✅ 团队介绍
- ✅ 无需后端，纯静态网站
- ✅ 快速加载，SEO 友好

## 许可证

© 2024 孝心圈. 保留所有权利.
