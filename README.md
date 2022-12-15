# README

# 项目地址[RockChinQ/QChatGPT](https://github.com/RockChinQ/QChatGPT)

本项目旨在为原项目提供一个简单的 Docker 部署方式，方便大家使用。

下述命令均在项目根目录下执行。

原项目地址：[RockChinQ/QChatGPT](https://github.com/RockChinQ/QChatGPT)

## 1. 安装 Docker和 Docker Compose

- [获取 Docker 桌面版 (已包含 Compose)](https://docs.docker.com/get-docker/)
- [中文](https://dockerdocs.cn/get-docker/index.html)

## 2. 下载所需要文件
`linux`系统可以直接使用loadFile.sh (已安装 git 和 wget)
```
chmod +x loadFile.sh && ./loadFile.sh 
```

`windows`可以下载[ITXTech](https://github.com/iTXTech/mirai-console-loader/releases/download/v2.1.2/mcl-2.1.2.zip)和[RockChinQ/QChatGPT](https://github.com/RockChinQ/QChatGPT)，把`requirements.txt`放入`bot`目录里面

最终效果如下，`bot`目录内是当前的[RockChinQ/QChatGPT](https://github.com/RockChinQ/QChatGPT)项目里面的内容,`mirai`目录内是[ITXTech](https://github.com/iTXTech/mirai-console-loader/releases/download/v2.1.2/mcl-2.1.2.zip)下载后解压到`mirai`里面

```
.
├── bot
│   ├── config-template.py
│   ├── LICENSE
│   ├── main.py
│   ├── pkg
│   ├── README.md
│   ├── requirements.txt
│   ├── res
│   ├── sensitive.json
│   └── tests
├── docker-compose.yaml
├── loadFile.sh
├── mirai
│   ├── LICENSE
│   ├── mcl
│   ├── mcl.cmd
│   ├── mcl.jar
│   └── README.md
├── _mirai.Dockerfile
└── _setup.Dockerfile
```
## 3. 配置 启动mirai

`docker compose run --rm mirai`

等待安装，并按照提示操作登录。(第一次失败的话就，`Ctrl + C`退出，再重来一次)

具体见[4.登录QQ](https://yiri-mirai.wybxc.cc/tutorials/01/configuration)

当机器人账号登录成功以后，执行

`autologin add <机器人QQ号> <机器人密码>`(必要)

`autologin setConfig <机器人QQ号> protocol ANDROID_PAD`(必要)

成功后, `Ctrl + C` 退出。

之后重新打开目录`bot`，根据`config-template.py`写一个`config.py`文件（`config.py`放在`bot`文件夹里面）
配置详细见[RockChinQ/QChatGPT](https://github.com/RockChinQ/QChatGPT)的`README`

## 4. 启动

`docker compose up ` 将在前台启动。

`docker compose up -d` 将在后台启动。

注意，只有在mirai执行成功的时候，bot不会戳，如果出错， `Ctrl + C`退出.
先输入`docker compose run --d mirai`执行mirai
再输入 `docker compose run --d bot` 执行机器人
