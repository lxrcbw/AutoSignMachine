# AutoSignMachine

## 运行 docker

```sh
# 构建
docker build -t lunnlew/auto-sign-machine:latest  -f docker/Dockerfile .
# 运行
docker run \
  --name auto-sign-machine \
  -d \
  -p 3003:3003 \
  -v /root/.AutoSignMachine:/root/.AutoSignMachine \
  -e enable_jingdong=true \
  -e enable_webui=true \
  lunnlew/auto-sign-machine:latest
# 停止
docker stop auto-sign-machine
# 删除
docker rm auto-sign-machine
# 强制删除
docker rm -f auto-sign-machine
# 日志
docker logs -f auto-sign-machine
```

其中暴露出的 3003 端口可用于访问 webUI

默认数据目录为`/root/.AutoSignMachine`,可以使用环境变量`-e SAVE_DATA_DIR=/root/.AutoSignMachine`来重新指定

默认配置文件名称结构为`[command].json`,例如`jingdong.json` ,可以使用环境变量`-e config_[command]=jingdong.json`来重新指定

## 任务环境变量文件.env

文件.env 可创建并放在代码根目录，与 commands、webUI 等同级

```text
  notify_pushplus_token=xxxxxxxxxxxxxx
  notify_sckey=xxxxxxxxxxxxxx
  notify_wechat_corpid=xxxxxxxxxxxxxx
  notify_wechat_corpsecret=xxxxxxxxxxxxxx
  notify_wechat_agentld=xxxxxxxxxxxxxx
  notify_tele_bottoken=xxxxxxxxxxxxxx
  notify_tele_chatid=xxxxxxxxxxxxxx
  notify_tele_url=xxxxxxxxxxxxxx
  ban_jingdong_tasks=xxxxxx,xxxxxx
```
