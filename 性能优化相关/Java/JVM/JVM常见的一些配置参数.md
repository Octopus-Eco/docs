### 1、JVM Heap 配置
JAVA_OPTS="$JAVA_OPTS -Xms12g -Xmx12g -Xmn6g -XX:SurvivorRatio=1"

注：指定jvm heapsize 最大(Xmx)和最小值(Xms)都为12GB，新生代最大(Xmn)6GB，XX:SurvivorRatio是制定新生代区(Young)内的Eden与Survivor0、Survivor1之间的倾斜比例，相当于Eden是S0、S1 大小的3倍。所以，Eden占新生代大小的3/6，S0和S1 每个占新生代的1.5/6。注意，两个幸存区永远是一样大的。

### 2、GC日志
JAVA_OPTS="$JAVA_OPTS -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Xloggc:/home/aplus/apache-tomcat-8.5.9/logs/gc.log"
注：指定打印垃圾收集日志(gc.log)

### 3、HeapDump日志
JAVA_OPTS="$JAVA_OPTS -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/${PATH}/apache-tomcat-8.5.8/logs"
注：指定当jvm出现OOM异常时将Heap内的快照Dump出一份文件

### 4、JMX监控
CATALINA_OPTS="$CATALINA_OPTS -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9999 -Dcom.sun.management.jmxremote.rmi.port=9999 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false 
-Djava.rmi.server.hostname=被监控机IP"

注：指定JMX的端口为9999，绑定RMI地址为被监控机的地址

 __上述是在$TOMCAT_HOME/bin/catalina.sh中配置的JAVA_OPTS参数，基于Oracle JDK1.8__