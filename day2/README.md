# 运行开源小说项目Novel

## 0. 克隆代码
```bash
git clone https://gitee.com/novel_dev_team/novel.git
```
## 1. 安装mysql7环境
```yaml
services:
  mysql:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      MYSQL_DATABASE: test1
      MYSQL_USER: devuser 
      MYSQL_PASSWORD: root
      # Add this to allow root to connect from anywhere
      MYSQL_ROOT_HOST: '%'
    ports:
      - "3306:3306"
    volumes:
      - ./mysql_data:/var/lib/mysql
      # Add custom MySQL configuration
      - ./my.cnf:/etc/mysql/conf.d/my.cnf
    command: --default-authentication-plugin=mysql_native_password

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - "8080:80"
    environment:
      PMA_HOST: mysql
      PMA_PORT: 3306
    depends_on:
      - mysql
```

## 2. 安装redis7环境
```yaml
services:
  redis:
    image: redis:7
    container_name: redis7
    command: redis-server --requirepass 123456 --bind 0.0.0.0
    ports:
      - "6379:6379"
    volumes:
      - ./redis_data:/data
    restart: unless-stopped
```

## 3. 修改配置文件

## 4. 安装mvn

## 5. 运行项目