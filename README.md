# docker套娃baota
优雅地使用 Docker 套娃纯净宝塔面板。

## 一、前言



能力有限，对github、Linux、docker等并不是特比的熟悉，基本上就是靠着文档+谷歌+实践慢慢学了些皮毛.

制作了本纯净版镜像

## 二、镜像特点
- 系统Debian 12
- 纯净9.5.0版本





## 三、配置信息

### 1.面板配置信息


- 面板默认登录地址：```http://{{ip地址}}:8888/btpanel```
- 面板默认用户名：```btpanel```
- 面板默认密码：```btpaneldocker```
- 面板默认端口：```8888```
- 面板默认安全入口：```/btpanel```

### 2.容器配置信息
- 容器ssh端口：```22```
- 密码：```btpaneldocker```
- 远程登录容器```ssh root@{{ip地址}} -p 22```

### 3 **注意**：部署后务必先修改如上信息！！！或者修改代码后自行构建使用！！！以防止被利用！！！

镜像仓库地址：[https://hub.docker.com/r/kissgun/baota](https://hub.docker.com/r/kissgun/baota)

代码仓库地址：[https://github.com/kissgun258/baota-docker](https://github.com/kissgun258/baota-docker)





## 四、通过 docker-compose.yml运行

```bash
services:
  baota:
    image: kissgun/baota
    container_name: baota
    privileged: true
    network_mode: host
    restart: unless-stopped
    volumes:
      - ./www/wwwroot:/www/wwwroot
      - ./www/vhost:/www/server/panel/vhost
      - ./www/letsencrypt:/www/letsencrypt
      - ./www/init.d:/www/init.d
```



