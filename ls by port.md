```
lsof -i :portNumber
lsof -i tcp:portNumber
lsof -i udp:portNumber
```

```
grep port /etc/services
```

```
fuser port/tcp
  port/tcp:   pid
ls -l /proc/24476/exe
ps aux | grep pid
(...)
```
