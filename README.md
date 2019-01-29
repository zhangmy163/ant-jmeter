## 简介

ant通过执行build.xml文件，来实现运行jmeter脚本，并生产报告

**注意**

```
build.xml:79: taskdef class org.programmerplanet.ant.taskdefs.jmeter.JMeterTask cannot be found
 using the classloader AntClassLoader[]
```

把文件jmeter下\extras\ant-jmeter-1.1.1.jar复制到的\lib目录下即可。

### 使用方法

1.如果jmeter脚本用到mysql的驱动，则需要将mysql-connector-java-5.1.7-bin.jar放在jmeter安装目录的lib下（如果没用到则不需要）

2.将jmeter-results-detail-report_vivian.xsl放在jmeter安装目录的extras下，也放一份在$testbase目录下

3.运行命令`ant -file build.xml -DTEST=$testdir -Djmeter.home=$jmeter_base_path -Dtestpath=$testbase/$testdir` 

#### e.g.

目录结构

```
~/test/
       jmeter-results-detail-report_vivian.xsl
       build.xml
       qa/
          testqa.jmx
       dev/
           testdev.jmx
```

运行命令：

`cd ~/test`

`ant -file build.xml -DTEST=qa -Djmeter.home=~/apache-jmeter-5.0 -Dtestpath=~/test/qa`

运行后~/test下会生成result目录，打开report.html即可看到运行结果报告
