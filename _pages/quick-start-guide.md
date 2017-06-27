---
permalink: /quick-start-guide/
title: "Raspberry Iot Sensor Kit"
---

# OpenTSDB && InfluxDB ver 1.2.0 설치 및 실행 메뉴얼
## 점검사항```/etc/profile -> export HBASE_HOME=/home/pi/work/hadoop/hbase-1.3.1$sudo apt-get install -y gnuplotopentsdb install -> ./configure ?```## JAVA8_JDK_INSTALL```$ sudo apt-get update && sudo apt-get install oracle-java8-jdk$ sudo update-alternatives --config java```## OpenTSDB+ Hbase 설치```$ mkdir -p ~/work/hadoop$ cd ~/work/hadoop$ wget https://archive.apache.org/dist/hbase/1.0.1.1/hbase-1.0.1.1-bin.tar.gz$ tar -xvf hbase-1.0.1.1-bin.tar.gz$ cd hbase-1.0.1.1/$ vim conf/hbase-env.sh --> export JAVA_HOME 수정 ex) export JAVA_HOME=/usr/$ hbase_rootdir=${TMPDIR-'/home/pi/work/hadoop/data'}/tsdhbase$ iface=lo`uname | sed -n s/Darwin/0/p`$ vim conf/hbase-site.xml```<pre>*** hbase-1.3.1 opentsdb로 데이터가 저장이 안됨(serial_win10_app.py) ***</pre>
   + hbase-site.xml `<configuration> tag 사이에 아래내용 입력`   + DIRECOTRY -> hbase ,zookeeper 실행시 저장할 디렉토리```<?xml version="1.0"?>     <?xml-stylesheet type="text/xsl" href="configuration.xsl"?>     <configuration>
       <property>         <name>hbase.rootdir</name>         <value>file:////home/pi/work/hadoop/hbase-1.0.1.1</value>       </property>       <property>         <name>hbase.zookeeper.property.dataDir</name>         <value>/home/pi/work/hadoop/zookeeper</value>        </property>
     </configuration>```<pre> sudo ./bin/start-hbase.sh </pre>
+ error like this```Java HotSpot(TM) Client VM warning: ignoring option PermSize=128m; support was removed in 8.0Java HotSpot(TM) Client VM warning: ignoring option MaxPermSize=128m; support was removed in 8.0```+ conf/hbase-env.sh 수정 (JDK8 이상) ```# Configure PermSize. Only needed in JDK7. You can safely remove it for JDK8+
two line remove or comment them#export HBASE_MASTER_OPTS="$HBASE_MASTER_OPTS -XX:PermSize=128m -XX:MaxPermSize=128m"#export HBASE_REGIONSERVER_OPTS="$HBASE_REGIONSERVER_OPTS -XX:PermSize=128m -XX:MaxPermSize=128m"```
+ GnuPlot 설치```$ cd ~/work$ sudo apt-get install -y gcc libgd2-xpm-devold) $sudo wget http://sourceforge.net/projects/gnuplot/files/gnuplot/4.6.3/gnuplot-4.6.3.tar.gzold) $tar -xvf gnuplot-4.6.3.tar.gz new) $sudo wget https://sourceforge.net/projects/gnuplot/files/gnuplot/5.0.6/gnuplot-5.0.6.tar.gznew) $tar -xvf gnuplot-5.0.6.tar.gz$ cd gnuplot-4.6.3$ sudo ./configure$ sudo make install$ sudo apt-get install -y dh-autoreconf```+ OpenTSDB 1.2.0 설치
```$ cd ~/work$ git clone git://github.com/OpenTSDB/opentsdb.git$ cd opentsdb$ sudo ./build.sh$ (sudo?) env COMPRESSION=NONE HBASE_HOME=/home/pi/work/hadoop/hbase-1.0.1.1 ./src/create_table.sh$ tsdtmp=${TMPDIR-'/home/pi/work/hadoop/data'}/tsd$ mkdir -p "$tsdtmp"```+ 실행<pre> ./build/tsdb tsd --port=4242 --staticroot=./build/staticroot --cachedir=/home/pi/work/opentsdb_cashe --auto-metric </pre>## influxDB-1.2.0 메뉴얼+ 설치```wget https://dl.influxdata.com/influxdb/releases/influxdb_1.2.0_armhf.debsudo dpkg -i influxdb_1.2.0_armhf.debsudo service influxdb start```+ 설정```$sudo vim /etc/influxdb/influxdb.conf```+ 에러   ```   ImportError: No module named logger   -> $ sudo pip install logger```
## 구조
```- database  - measurement    - field    - tag```* database : DBMS 의 database 와  같음* measurement : DBMS 의 table 과 같음* time : timestamp (nano sec)* field : reading 로 구성* tags : 인덱스 값으로 검색에 사용됨
## 사용법
```pythonimport tsdb
tr = tsdb.Transaction(<measurement>)tr.write(value=<int, long, float>, meta=<str>, tag=<dict>, timestamp=<int, long>)tr.flush()```1. tsdb.py 를 import 한다.2. tr.Transaction() 함수 : series 을 지정한다 (해당 series 가 없어도 됨)3. tr.write() 함수 : 저장할 값을 넘김, 저장하지 않을 값은 비워도 됨4. tr.flush() 함수 : influxdb 에 저장
### HTTP 포트번호  - 8086 (API 포트, SQL 제공)  - 8083 (Admin 포트, 이제부터는 Grafana admin 연결 사용하여 더 이상 사용안함)
# Grafana
<del>## 설치방법(ver3.1.1)wget https://github.com/fg2it/grafana-on-raspberry/raw/master/jessie/v3.1.1/grafana_3.1.1-1470786449_armhf.debsudo dpkg -i grafana_3.1.1-1470786449_armhf.debsudo service grafana-server start</del>
## 설치방법(ver4.1.2)```wget https://grafanarel.s3.amazonaws.com/builds/grafana_4.1.2-1486989747_amd64.debsudo dpkg -i grafana_4.1.2-1486989747_amd64.debsudo service grafana-server start```
## 설치방법(ver4.1.2) base on rapsberrypi jessie ver (2017-04-10)```$ wget https://github.com/fg2it/grafana-on-raspberry/releases/download/v4.1.2/grafana_4.1.2-1487023783_armhf.deb$ sudo apt-get install -y adduser libfontconfig$ sudo dpkg -i grafana_4.1.2-1487023783_armhf.deb$ sudo service grafana-server start```
## 정보
* grafana 접속 포트 : 3000* 계정 : admin / admin
* [참고자료](https://github.com/fg2it/grafana-on-raspberry)
### influxDB   <del>- https://docs.influxdata.com/influxdb/v0.9/query_language/schema_exploration/</del>  https://docs.influxdata.com/influxdb/v1.2/query_language/schema_exploration/
