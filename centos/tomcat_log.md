## tomcat 日志定时删除

crontab -e

直接这个该命令，添加一个定时任务计划

00 00 * * * /bin/find /usr/tomcat/apache-tomcat-8.5.35/logs -type f -mtime +7 | xargs rm -f  &>/dev/null

在其中添加


crontab -l

查看定时任务

service crond reload

重新载入配置  前提是crond已经启动