# 原本链部署文档

## 原本链公共域名服务
```
https://api.yuanbenlian.com
```

## 注意事项

```
1. 原本链节点要经过认证之后才能访问，所以，如果贵公司要启动一个新的节点的话，请把贵公司节点的公钥发送过来，并备注，谢谢
2. 公钥位置在kdata/config/priv_validator.json文件的pub_key中
3. 现在节点使用自带数据库，如果想用公司内部的数据库，请修改配置文件，详情knode.yaml
4. 如果要用原本链公共服务，请把贵公司SDK生成的公钥发送过来
```

## 配置文件介绍

```
1. genesis.json
* kdata/config/genesis.json
* 为创世块文件，不可修改

2. 区块链config.toml
* kdata/config/config.toml
* 不想看终端区块打印信息，可以修改log_level＝"error"

3. knode.yaml
* kdata/config/knode.yaml
* 原本链节点API配置文件  可以修改log_level和debug两个选项
* 如果贵公司使用代理反向得到的外网地址请配置 `externalip: 外网的IP` 用于其它节点的发现
* 如果想用自己的数据库的话，请修改mysqlDb选项换成自己的数据库地址

4. node_key.json
* kdata/config/node_key.json
* 该文件为系统生成的节点文件
* 请把kdata/config/priv_validator.json中的私钥替换掉kdata/config/node_key.json中的私钥,用于节点的认证

5. priv_validator.json
* kdata/config/priv_validator.json
* 私钥文件，请妥善保管

```

## 系统要求

```
1. linux操作系统
2. 需要提供外网可访问的接口(46656/udp,46657/tcp,9000/tcp)
3. 至少2M带宽
4. 系统内存至少4G
5. 系统存储至少100G
```

## 部署工具

```
git clone https://git.dev.yuanben.org/scm/unv/universe-dp.git --depth=1
请把`config`中的task文件放到`/usr/local/bin`中以便下一步使用
```

## 项目启动

```
1. 检查项目依赖依赖，登陆镜像仓库
task login
task pull

2. 安装docker
如果服务器安装了docker跳过即可，没有则执行task install_docker进行安装

3. 初始化dev项目|初始化pro项目
task dev | task pro
dev 启动一个本地的私有链，不连接原本链
pro 启动一个连接联盟链的节点,需要把公钥给原本链认证
初始化项目后，请按照配置文件介绍，将node_key.json的内容进行替换

4. 单独启动kchain测试节点和原本链的联通情况
task kchain
如果日志出现联系管理员，请按照注意事项中的提示，将公钥发送给原本进行注册。
如果日志打印出现Executed block 和 Committed state 表示节点联通正常。crtl+c退出，进行下面的部署

5.启动节点
task s
如果出现"docker-compose": executable file not found in $PATH，请执行task deps

```

## 项目命令介绍
```
1. task d 删除项目
2. task s 启动项目
3. task ss 拉取镜像重启项目
4. task kchain 单独启动kchain测试和原本链的联通情况
5. task ls 查看当前启动的服务
6. task log 打印当前服务的日志,如果想单独查看每一个服务的日志，请用docker logs
7. task rm_none 删除镜像名称为none的镜像
8. task rm_stop 删除所有的服务，包括正在运行的和停止运行的
9. task login 登陆原本链镜像库
```
