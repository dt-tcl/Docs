# Docker(CentOS 7) 환경에 Hadoop 설치

## 실행 서비스
master : namenode, resource manager
slave01 : secondary namenode, nodemanager, datanode
slave02 : nodemanager, datanode
slave03 : nodemanager, datanode

## CentOS 7 Base 이미지 생성
### 1) Dockerfile 생성
```bash
[suetest723@node1 ~]$ sudo yum -y install docker
[suetest723@node1 ~]$ mkdir -p docker-images/centos7-base
[suetest723@node1 ~]$ cd docker-images/centos7-base
[suetest723@node1 centos7-base]$ vi Dockerfile
Dockerfile
FROM docker.io/centos:7.4.1708
# 사용자 지정
USER root
# 언어셋 설치
RUN yum clean all \
 && yum repolist \
 && yum -y update \
 && sed -i "s/en_US/all/" /etc/yum.conf  \
 && yum -y reinstall glibc-common 
# 기본적으로 필요한 OS 패키지를 설치한다.
RUN  yum -y install tar unzip vi vim telnet net-tools curl openssl \
 && yum -y install apr apr-util apr-devel apr-util-devel \
 && yum -y install elinks locate python-setuptools \
 && yum clean all
ENV LANG=ko_KR.utf8 TZ=Asia/Seoul
# 컨테이너 실행시 실행될 명령
CMD ["/bin/bash"]
```

### 2) Image 생성
```bash
[suetest723@node1 centos7-base]$ sudo docker build -t centos7-base:7.4 .
Sending build context to Docker daemon 2.048 kB
Step 1 : FROM docker.io/centos:7
 ---> 0584b3d2cf6d
Step 2 : USER root
 ---> Running in 070a0180b355
 ---> ce587d6b302b
...

# 생성된 이미지 확인
[suetest723@node1 centos7-base]$ sudo docker images
REPOSITORY           TAG                 IMAGE ID            CREATED              SIZE
centos7-base        7.4              ae734322575e        About a minute ago      557MB
```

### 3) 컨테이너 실행
```bash
# 컨테이너 실행하고 바로 터미널로 접속
[suetest723@node1 centos7-base]$ sudo docker run -ti --name=centos7-base centos7-base:7.4
# 컨테이너 내부
[root@7a60d11c5cc2 /]# hostname
7a60d11c5cc2
[root@7a60d11c5cc2 /]# cat /etc/redhat-release
CentOS Linux release 7.6.1810 (Core) 
[root@7a60d11c5cc2 /]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.6  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:06  txqueuelen 0  (Ethernet)
        RX packets 8  bytes 656 (656.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
# 컨테이너 종료
[root@7a60d11c5cc2 /]# exit
```

## Hadoop 설치
### 1) 컨테이너 실행
```bash
[suetest723@node1 hadoop-2.9.0]$ sudo docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
centos7-base        7.4                 ae734322575e        19 hours ago        557MB
[suetest723@node1 hadoop-2.9.0]$ sudo docker run -ti --name=centos7-base centos7-base:7.4
```

### 2) Java 설치
```bash
[root@fe721fca7bb5 /]# yum install java-1.8.0-openjdk, java-1.8.0-openjdk-devel
[root@fe721fca7bb5 /]# java -version
[root@fe721fca7bb5 /]# javac -version
```

### 3) Hadoop 2.9.1 설치
```bash
[root@fe721fca7bb5 /]# yum install wget
[root@fe721fca7bb5 /]# cd /home
[root@fe721fca7bb5 /]# mkdir sue
[root@fe721fca7bb5 /]# cd sue/
[root@fe721fca7bb5 sue]# wget http://mirrors.sonic.net/apache/hadoop/common/hadoop-2.9.1/hadoop-2.9.1.tar.gz
[root@fe721fca7bb5 sue]# tar xvzf hadoop-2.9.1.tar.gz
```

### 4) 환경 변수 설정
```bash
[root@fe721fca7bb5 sue]# vi ~/.bashrc
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el7_6.x86_64
export HADOOP_HOME=/home/sue/hadoop-2.9.1
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export PATH=$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$PATH
export CLASS_PATH=$JAVA_HOME/lib:$CLASS_PATH
[root@7a60d11c5cc2 sue]# source ~/.bashrc

### 5) hadoop 2.9.1 설정
[root@fe721fca7bb5 hadoop]# cd $HADOOP_CONF_DIR

[root@fe721fca7bb5 hadoop]# vi hadoop-env.sh
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el7_6.x86_64
export HADOOP_HOME=/home/sue/hadoop-2.9.1
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export YARN_CONF_DIR=$HADOOP_HOME/etc/hadoop

[root@fe721fca7bb5 hadoop]# vi yarn-env.sh
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el7_6.x86_64
export HADOOP_HOME=/home/sue/hadoop-2.9.1
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export YARN_CONF_DIR=$HADOOP_HOME/etc/hadoop

[root@fe721fca7bb5 hadoop]# vi slaves
slave01
slave02
slave03

[root@fe721fca7bb5 hadoop]# vi core-site.xml
<configuration>
   <property>
      <name>fs.default.name</name>
      <value>hdfs://master:9000</value>
   </property>
   <property>
      <name>hadoop.tmp.dir</name>
      <value>/home/sue/hadoop-2.9.1/hdfs/</value>
   </property>
</configuration>

[root@fe721fca7bb5 hadoop]# mkdir /home/sue/hadoop-2.9.1/hdfs/

[root@fe721fca7bb5 hadoop]# vi hdfs-site.xml
<configuration>
   <property>
      <name>dfs.replication</name>
      <value>2</value>
   </property>
   <property>
      <name>dfs.permissions</name>
      <value>false</value>
   </property>
   <property>
      <name>dfs.namenode.secondary.http-address</name>
      <value>slave01:50090</value>
   </property>
   <property>
      <name>dfs.namenode.secondary.https-address</name>
      <value>slave01:50091</value>
   </property>
</configuration>

[root@fe721fca7bb5 hadoop]# vi mapred-site.xml
<configuration>
   <property>
      <name>mapreduce.framework.name</name>
      <value>yarn</value>
   </property>
</configuration>

[root@fe721fca7bb5 hadoop]# vi yarn-site.xml
<configuration>
   <property>
      <name>yarn.nodemanager.aux-services</name>
      <value>mapreduce_shuffle</value>
   </property>
   <property>
      <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
      <value>org.apache.hadoop.mapred.ShuffleHandler</value>
   </property>
   <property>
      <name>yarn.resourcemanager.resource-tracker.address</name>
      <value>master:8025</value>
   </property>
   <property>
      <name>yarn.resourcemanager.scheduler.address</name>
      <value>master:8030</value>
   </property>
   <property>
      <name>yarn.resourcemanager.address</name>
      <value>master:8040</value>
   </property>
   <property>
      <name>yarn.resourcemanager.webapp.address</name>
      <value>master:8088</value>
   </property>
</configuration>
```

### 5) ssh 설치 및 설정
```bash
[root@fe721fca7bb5 hadoop]# yum -y install openssh-server openssh-clients openssh-askpass
[root@fe721fca7bb5 hadoop]# cd ~/
[root@fe721fca7bb5 hadoop]# ssh-keygen -t rsa
[root@fe721fca7bb5 hadoop]# cd .ssh
[root@fe721fca7bb5 hadoop]# cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
[root@fe721fca7bb5 hadoop]# chmod 644 ~/.ssh/authorized_keys
[root@fe721fca7bb5 hadoop]# mkdir /var/run/sshd
```

### 6) Hadoop docker 이미지 생성
```bash
ctrl + p, ctrl + q
[suetest723@node1 ~]$ sudo docker commit centos7-base centos7:hadoop
[suetest723@node1 ~]$ sudo docker rm -f centos7-base
```

### 7) Docker 이미지를 이용한 hadoop node(master, slave01, slave02, slave03) 생성
```bash
[suetest723@node1 ~]$ sudo docker run --privileged -d -h master --name master -p 50070:50070 centos7:hadoop init
[suetest723@node1 ~]$ sudo docker exec -it master bash
ctrl + p, ctrl + q
[suetest723@node1 ~]$ sudo docker run --privileged -d -h slave01 --name slave01 --link master:master centos7:hadoop init
[suetest723@node1 ~]$ sudo docker exec -it slave01 bash
ctrl + p, ctrl + q
[suetest723@node1 ~]$ sudo docker run --privileged -d -h slave02 --name slave02 --link master:master centos7:hadoop init
[suetest723@node1 ~]$ sudo docker exec -it slave02 bash
ctrl + p, ctrl + q
[suetest723@node1 ~]$ sudo docker run --privileged -d -h slave03 --name slave03 --link master:master centos7:hadoop init
[suetest723@node1 ~]$ sudo docker exec -it slave03 bash
ctrl + p, ctrl + q
```

### 8) Hadoop node IP 설정
```bash
# container ip 조사
[suetest723@node1 ~]$ sudo docker inspect -f '{{ .NetworkSettings.IPAddress }}' master
172.17.0.2
[suetest723@node1 ~]$ sudo docker inspect -f '{{ .NetworkSettings.IPAddress }}' slave01
172.17.0.3
[suetest723@node1 ~]$ sudo docker inspect -f '{{ .NetworkSettings.IPAddress }}' slave02
172.17.0.4
[suetest723@node1 ~]$ sudo docker inspect -f '{{ .NetworkSettings.IPAddress }}' slave03
172.17.0.5

# 각 컨테이너(master,slave01,slave02,slave03)에 접속해서 host 파일 업데이트
[suetest723@node1 ~]$ sudo docker exec -it master bash
[root@master /]# vi /etc/hosts
172.17.0.2	master
172.17.0.3	slave01
172.17.0.4	slave02
172.17.0.5	slave03

ctrl + p, ctrl + q
```

### 9) 각 컨테이너(master,slave01,slave02,slave03)에 접속해서 SSH 설정
```bash
[suetest723@node1 ~]$ sudo docker attach master
[root@master /]# systemctl restart sshd
ctrl + p, ctrl + q
```

### 10) master 접속해서 namenode directory 설정 및 hadoop 시작
```bash
[root@master /]# mkdir -p /home/sue/hadoop-2.9.1/hdfs/dfs/name
[root@master /]# hadoop namenode -format
[root@master /]# start-all.sh

# 각 노드에 실행중인 서비스 확인
[root@master ~]# jps
8857 NameNode
889 Jps
6892 ResourceManager
[root@slave01 ~]# jps
4944 DataNode
5026 SecondaryNameNode
8230 Jps
5117 NodeManager
[root@slave02 ~]# jps
3573 NodeManager
4455 Jps
3471 DataNode
[root@slave03 ~]# jps
3029 Jps
2262 DataNode
2364 NodeManager

# hdfs server 정보 확인
[root@master /]# /home/sue/hadoop-2.9.1/binbin/hadoop dfsadmin -report
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.
Configured Capacity: 257655189504 (239.96 GB)
Present Capacity: 229080600576 (213.35 GB)
DFS Remaining: 229080588288 (213.35 GB)
DFS Used: 12288 (12 KB)
DFS Used%: 0.00%
Under replicated blocks: 0
Blocks with corrupt replicas: 0
Missing blocks: 0
Missing blocks (with replication factor 1): 0
Pending deletion blocks: 0
-------------------------------------------------
Live datanodes (3):
Name: 172.17.0.3:50010 (slave01)
Hostname: slave01
Decommission Status : Normal
Configured Capacity: 85885063168 (79.99 GB)
DFS Used: 4096 (4 KB)
Non DFS Used: 9524862976 (8.87 GB)
DFS Remaining: 76360196096 (71.12 GB)
DFS Used%: 0.00%
DFS Remaining%: 88.91%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 1
```

## WordCount테스트
```bash
[root@master ~]# hdfs dfs -mkdir -p /user/root/input
[root@master ~]# hdfs dfs -put ~/README.txt /user/root/input/
[root@master ~]# hadoop jar /home/sue/hadoop-2.9.1/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.9.1.jar wordcount input output
19/07/01 09:31:20 INFO client.RMProxy: Connecting to ResourceManager at master/172.17.0.2:8040
19/07/01 09:31:21 INFO input.FileInputFormat: Total input files to process : 1
19/07/01 09:31:22 INFO mapreduce.JobSubmitter: number of splits:1
19/07/01 09:31:22 INFO Configuration.deprecation: yarn.resourcemanager.system-metrics-publisher.enabled is deprecated. Instead, use yarn.system-metric
s-publisher.enabled
19/07/01 09:31:22 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1561971773890_0001
19/07/01 09:31:23 INFO impl.YarnClientImpl: Submitted application application_1561971773890_0001
19/07/01 09:31:23 INFO mapreduce.Job: The url to track the job: http://master:8088/proxy/application_1561971773890_0001/
19/07/01 09:31:23 INFO mapreduce.Job: Running job: job_1561971773890_0001
19/07/01 09:31:34 INFO mapreduce.Job: Job job_1561971773890_0001 running in uber mode : false
19/07/01 09:31:34 INFO mapreduce.Job:  map 0% reduce 0%
19/07/01 09:31:42 INFO mapreduce.Job:  map 100% reduce 0%
19/07/01 09:31:51 INFO mapreduce.Job:  map 100% reduce 100%
19/07/01 09:31:52 INFO mapreduce.Job: Job job_1561971773890_0001 completed successfully
19/07/01 09:31:52 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=1836
                FILE: Number of bytes written=398775

                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=1476
                HDFS: Number of bytes written=1306
                HDFS: Number of read operations=6
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
        Job Counters 
                Launched map tasks=1
                Launched reduce tasks=1
                Data-local map tasks=1
                Total time spent by all maps in occupied slots (ms)=5639
                Total time spent by all reduces in occupied slots (ms)=5481
                Total time spent by all map tasks (ms)=5639
                Total time spent by all reduce tasks (ms)=5481
                Total vcore-milliseconds taken by all map tasks=5639
                Total vcore-milliseconds taken by all reduce tasks=5481
                Total megabyte-milliseconds taken by all map tasks=5774336
                Total megabyte-milliseconds taken by all reduce tasks=5612544
        Map-Reduce Framework
                Map input records=31
                Map output records=179
                Map output bytes=2055
                Map output materialized bytes=1836
                Input split bytes=110
                Combine input records=179
                Combine output records=131
                Reduce input groups=131
                Reduce shuffle bytes=1836
                Reduce input records=131
                Reduce output records=131
                Spilled Records=262
                Shuffled Maps =1
                Failed Shuffles=0
                Merged Map outputs=1
                GC time elapsed (ms)=302
                CPU time spent (ms)=1460
                Physical memory (bytes) snapshot=446984192
                Virtual memory (bytes) snapshot=3953954816
                Total committed heap usage (bytes)=339738624
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=1366
        File Output Format Counters 
                Bytes Written=1306

[root@master ~]# hdfs dfs -ls /user/root/output
Found 2 items
-rw-r--r--   2 root supergroup          0 2019-07-01 09:31 /user/root/output/_SUCCESS
-rw-r--r--   2 root supergroup       1306 2019-07-01 09:31 /user/root/output/part-r-00000
[root@master ~]# cat README.txt 
For the latest information about Hadoop, please visit our website at:

   http://hadoop.apache.org/core/

and our wiki, at:

   http://wiki.apache.org/hadoop/

This distribution includes cryptographic software.  The country in 
which you currently reside may have restrictions on the import, 
possession, use, and/or re-export to another country, of 
encryption software.  BEFORE using any encryption software, please 
check your country's laws, regulations and policies concerning the
import, possession, or use, and re-export of encryption software, to 
see if this is permitted.  See <http://www.wassenaar.org/> for more
information.

The U.S. Government Department of Commerce, Bureau of Industry and
Security (BIS), has classified this software as Export Commodity 
Control Number (ECCN) 5D002.C.1, which includes information security
software using or performing cryptographic functions with asymmetric
algorithms.  The form and manner of this Apache Software Foundation
distribution makes it eligible for export under the License Exception
ENC Technology Software Unrestricted (TSU) exception (see the BIS 
Export Administration Regulations, Section 740.13) for both object 
code and source code.

The following provides more details on the included cryptographic
software:
  Hadoop Core uses the SSL libraries from the Jetty project written 
by mortbay.org.
[root@master ~]# hdfs dfs -cat /user/root/output/part-r-00000  
(BIS),  1
(ECCN)  1
(TSU)   1
(see    1
5D002.C.1,      1
740.13) 1
<http://www.wassenaar.org/>     1
Administration  1
Apache  1
BEFORE  1
BIS     1
Bureau  1
Commerce,       1
Commodity       1
Control 1
Core    1
Department      1
ENC     1
Exception       1
Export  2
For     1
Foundation      1
Government      1
Hadoop  1
Hadoop, 1
Industry        1
Jetty   1
License 1
Number  1
Regulations,    1
SSL     1
Section 1
Security        1
See     1
Software        2
Technology      1
The     4
This    1
U.S.    1
Unrestricted    1
about   1
algorithms.     1
and     6
and/or  1
another 1
any     1
as      1
asymmetric      1
at:     2
both    1
by      1
check   1
classified      1
code    1
code.   1
concerning      1
country 1
country's       1
country,        1
cryptographic   3
currently       1
details 1       
```
