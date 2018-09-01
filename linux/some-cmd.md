## 日期转时间戳
```
date -d '2017-12-20 17:00' +%s
```

## 查看系统日志
```
# http://blog.csdn.net/zstack_org/article/details/56274966

sudo journalctl --system

sudo journalctl --system --since "2017-12-20 16:00:00"

journalctl --since "2015-01-10" --until "2015-01-11 03:00"

journalctl -xb
```

## 查看linux内核加载的模块
```
lsmod
```

## boot加载的模块
```
/etc/modules
/etc/modules-load.d/
```

