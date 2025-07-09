# docker套娃baota
优雅地使用 Docker 套娃纯净宝塔面板。

## 一、前言



能力有限，对github、Linux、docker等并不是特比的熟悉，基本上就是靠着文档+谷歌+实践慢慢学了些皮毛，所以有不周全之处还请见谅，也希望各位前辈们多多指教。

初衷是每次部署宝塔面板的安装过程都非常繁琐和漫长，考虑到docker的便捷性，每次部署只需要一键拉取和部署即可，方便快捷，简单省事，无需等待每次部署环境的漫长过程。

**另一方面，前段时间，baota后台上传数据的事情闹得沸沸扬扬，包括网友发现，连海外版本的aapanel也会在凌晨的时候上传数据，引起了很多小伙伴的担心。**

制作了本纯净版镜像

## 二、镜像特点

- 纯净9.5.0版本
- 全程自动安装依赖
- 自动安装宝塔面板、环境、插件
- 自动修改默认面板端口、用户名、密码、安全入口
- 自动配置镜像ssh
- 自动同意首次登陆的用户协议
- 纯净版基于官方代码、仅做通信剥离、代码未加密、未添加任何新增代码
- 剥离了所有与baota官方的通信、上报、下发；并且不与纯净版服务器通信；
- 提升为企业会员，免费使用软件商店中的所有[企业版插件]、[专业版插件]、[运行环境]、[免费插件]、[宝塔插件]；部分[第三方应用]安装可能会失败




## 三、如何部署

### 1.面板配置信息


- 面板默认登录地址：```http://{{ip地址}}:10808/kissgun```
- 面板默认用户名：```admin```
- 面板默认密码：```dockerbaota```
- 面板默认端口：```10808```
- 面板默认安全入口：```/kissgun```

### 2.容器配置信息
- 容器ssh端口：```1072```
- 密码：```dockerbaota```
- 远程登录容器```ssh root@{{ip地址}} -p 1072```

**注意**：部署后务必先修改如上信息！！！或者修改代码后自行构建使用！！！以防止被利用！！！

镜像仓库地址：[暂时没有后期推送]()

代码仓库地址：[https://github.com/kissgun258/baota-docker](https://github.com/kissgun258/baota-docker)





### 2.通过 docker-compose.yml运行

```bash
services:
  baota:
    image: 暂时没有，后期推送
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



