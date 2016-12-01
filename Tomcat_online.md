##生产环境Tomcat需要修改的配置

一、 catilina.sh
```
JAVA_OPTS="-server -Xms1024m -Xmx1024m -XX:PermSize=192m -XX:MaxPermSize=192m"
```

二、 对catalina.out日志做每日切分
```
使用cronolog工具分割
A、 cronolog工具下载
官方URL：http://cronolog.org/download/index.html
B、 cronolog编译安装
[TSP@tsp-dev-webservice ~]$ tar xvf cronolog-1.6.2.tar.gz
[TSP@tsp-dev-webservice cronolog-1.6.2]$ ./configure
[TSP@tsp-dev-webservice cronolog-1.6.2]$ make
[TSP@tsp-dev-webservice cronolog-1.6.2]$ sudo make install
C、 修改Tomcat启动脚本catalina.sh 
a、 修改输出日志路径
修改：
 if [ -z "$CATALINA_OUT" ] ; then
       CATALINA_OUT="$CATALINA_BASE"/logs/catalina.out
fi
为：
    if [ -z "$CATALINA_OUT" ] ; then
      CATALINA_OUT="$CATALINA_BASE"/logs/catalina.%Y-%m-%d.out
fi
b、 删除生成日志文件
注释：
touch "$CATALINA_OUT"
   为：
#touch "$CATALINA_OUT"
c、 修改启动脚本参数
修改：
      org.apache.catalina.startup.Bootstrap "$@" start \
      >> "$CATALINA_OUT" 2>&1 "&"
    为：
      org.apache.catalina.startup.Bootstrap "$@" start 2>&1 \
      | /usr/local/sbin/cronolog "$CATALINA_OUT" >> /dev/null &
```

三、 配置tomcat-users方便管理

四、 log4j的动态加载配置
