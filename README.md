# Docker Fly

docker build repo for v2fly

https://hub.docker.com/r/v2fly/v2fly-core

# docker run command
- ERROR :invalid user: VMessAEAD is enforced and a non VMessAEAD connection is received
- add V2RAY_VMESS_AEAD_FORCED=false
- `sudo docker run -d --name v2ray -e V2RAY_VMESS_AEAD_FORCED=false -v /etc/v2ray:/etc/v2ray -p 16821:16821 v2fly/v2fly-core`


# V2ray config example：
```
{
        "log": {
                "access": "/var/log/v2ray/access.log",
                "error": "/var/log/v2ray/error.log",
                "loglevel": "warning"
        },
        "inbounds": [{
                "port": 16821,
                "protocol": "vmess",
                "settings": {
                        "clients": [{
                                "id": "5a798d35-fb0b-40d8-9ce0-ddcec0da311a",
                                "level": 1,
                                "alterId": 64
                        }]
                }
        }],

        "outbounds": [{
                "protocol": "freedom"
        }]
}
```

# error info

- 问题描述：rejected Proxy|VMess|Encoding: invalid user
- 解决方案使用以下命令同步服务器与客户端的时间
```
root@racknerd-3ada11:~# ntpdate -u time.nist.gov
14 Nov 02:11:42 ntpdate[24551]: adjust time server 132.163.96.4 offset 0.000090 sec
```
