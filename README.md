# mayfly-go-easy
# 部署 80端口，该端口到config.yaml中改
# 端口占用使用lsof -i :80 后kill进程号
git clone https://github.com/skVPN/mayfly-go-easy.git && cd mayfly-go-easy && sh start.sh

# 缺省密码: admin/admin123.          ---(记得有这个.)

## https证书生成key：这里举例 myip.fun 这个域名

* 仓库地址：

https://github.com/acmesh-official/acme.sh

* 1.安装
curl https://get.acme.sh | sh -s email=yourmail@126.com

* 2.生成cert

"/root/.acme.sh"/acme.sh --issue -d myip.fun  -d www.myip.fun --nginx --force  

* 3.nginx可用的pem

acme.sh --install-cert -d myip.fun \
--key-file       /root/mayfly-go-easy/key.pem  \
--fullchain-file  /root/mayfly-go-easy/cert.pem \
--reloadcmd     "service nginx reload"

停掉nginx,service stop nginx
* 3 添加到config.yml里面

  tls:
    enable: false
    key-file: ./default.key
    cert-file: ./default.pem