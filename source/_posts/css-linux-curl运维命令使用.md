---
title: '[linux]curl运维命令使用'
date: 2017-01-24 15:40:15
tags:
---

#### 查看curl的响应时间
---
```
curl -o /dev/null -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "http://www.qq.com"

-w 格式化输出curl请求的各个参数，这里用到了（时间单位为秒）：
time_namelookup DNS寻址时间
time_connect  DNS寻址时间+建立连接时间
time_starttransfer  DNS寻址时间+建立连接时间+传输数据时间
time_total    DNS寻址时间+建立连接时间+传输数据时间+关闭连接时间
speed_download  下载速度

-o 为输出内容的位置，如果想记录下来就写文件名称
-s 静默模式，不显示连接等信息
```
效果如下：
[![图片](/images/shell_curl.png)](/images/shell_curl.png)