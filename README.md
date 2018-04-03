# 原本链部署文档


## 注意事项

```
1. 原本链节点要经过认证之后才能访问，所以，如果贵公司要启动一个新的节点的话，请把贵公司节点的公钥发送过来，并备注，谢谢
2. 公钥位置在kdata/config/priv_validator.json文件的pub_key中
```

## 配置文件介绍

```
1. genesis.json
kdata/config/genesis.json
为创世块文件，不可修改

2. 区块链config.toml
kdata/config/config.toml
如果不想产生空区块,可以修改consensus.wal_light=true
不想看区块信息，可以修改log_level＝"error"

3. knode.yaml
kdata/config/knode.yaml
原本链节点API配置文件  可以修改log_level和debug两个选项
```

## 系统要求

```
1. linux操作系统
2. 需要提供外网可访问的接口(46656/udp,46657/tcp,9000/tcp)
3. 至少2M带宽
4. 系统内存至少4G
5. 系统存储至少500G
```

## 部署工具

```
git clone https://git.dev.yuanben.org/scm/unv/universe-dp.git --depth=1
请把`config`中的task文件放到`/usr/local/bin`中以便下一步使用
```

## 项目启动

```
1. 检查docker依赖
task deps

2. 拉取镜像
task pull

3. 初始化dev项目|初始化pro项目
task init_dev | task init_pro
init_dev 启动一个本地的私有链，不链接联盟链
init_pro 启动一个连接联盟链的节点,需要把公钥给原本链这边帮助认证

4. 运行项目
task  start

5. 查看状态
task ls

6. 查看日志
task logs
```

## 测试地址

```
119.23.22.129:9000
47.254.129.188:9000
http://47.254.129.188:9000/v1/metadata/1NHKIJVSBOKZJG6MXJ47KD6I9ZRKOHHQ5NXVCL12MNRHLWQZTB
http://119.23.22.129:9000/v1/metadata/1NHKIJVSBOKZJG6MXJ47KD6I9ZRKOHHQ5NXVCL12MNRHLWQZTB
http://119.23.22.129:9000/v1/license/cc

多个节点测试数据同步情况，注意事项在最上面
```