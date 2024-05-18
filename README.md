<img alt="iptv-checker" src="https://github.com/zhimin-dev/iptv-checker-web/blob/main/src/assets/icon.png" height=80>

# iptv-checker

本项目拆成2个项目

- 前端[iptv-checker-web:v3.2.0](https://github.com/zhimin-dev/iptv-checker-web),提供iptv-checker后台页面
- 后端[iptv-checker-rs:v3.2.0](https://github.com/zhimin-dev/iptv-checker-rs),提供iptv的cmd命令以及web api


## docker本地打包

先将下面3个项目clone到本地(比如放在node文件夹下)，下面为文件夹目录示例

- node
  - iptv-checker
  - iptv-checker-web
  - iptv-checker-rs

```bash
cd node # 进入node文件夹
docker build -f iptv-checker/dockerfile -t ipserver . # 执行build
docker run -d -p 8081:8089 --name myIp ipserver # 运行
```

### Docker官方包使用方法

[DockerHub](https://hub.docker.com/r/zmisgod/iptvchecker)

按照下面的命令运行docker版本的iptv-checker

```bash
docker pull zmisgod/iptvchecker
docker run -d -p 8081:8089 --name myIp zmisgod/iptvchecker
```

再打开浏览器访问`http://127.0.0.1:8081/`即可

### Docker本地打多平台包方法

```bash
docker buildx create --name mybuilder
docker buildx inspect --bootstrap
docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t zmisgod/iptvchecker:latest --push -f iptv-checker/dockerfile . 
```

### Docker-Compose 部署

```bash
docker-compose up -d
```

## 更新日志

- 3.2.0
  - 支持关键词匹配
  - 支持超时时间配置
- 3.1.1
  - 修复后台检查后cpu增高的问题
- 3.1.0
  - 支持任务编辑
  - 支持任务立即执行
- 3.0.0
  - 支持后台检查

## 联系

[知敏博客](https://zmis.me/user/zmisgod)
