- jdk 설치

```
sudo apt-get update
sudo apt-get install scala
```

- scala 실행
```
scala

ithingvvv@instance-1:~$ scala
Welcome to Scala 2.11.12 (OpenJDK 64-Bit Server VM, Java 11.0.15).
Type in expressions for evaluation. Or try :help.

scala> print("hello world")
hello world

```

- spark 설치
https://spark.apache.org/downloads.html

```
# 설치파일을 다운로드 받습니다.
$ wget https://dlcdn.apache.org/spark/spark-3.2.1/spark-3.2.1-bin-hadoop3.2.tgz

# 압축을 풉니다.
$ tar -xvzf spark-3.2.1-bin-hadoop3.2.tgz

# 스파크 디렉토리명을 spark-3.2.1-bin-hadoop3.2에서 spark로 변경합니다.
mv spark-3.2.1-bin-hadoop3.2/ spark/
```

```
ithingvvv@instance-1:~/spark$ cd bin/
ithingvvv@instance-1:~/spark/bin$ ./spark-shell 
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.spark.unsafe.Platform (file:/home/ithingvvv/spark/jars/spark-unsafe_2.12-3.2.1.jar) to constructor java.nio.DirectByteBuffer(long,int)
WARNING: Please consider reporting this to the maintainers of org.apache.spark.unsafe.Platform
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
22/05/17 06:03:50 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Spark context Web UI available at http://instance-1.us-west4-b.c.avid-stone-347506.internal:4040
Spark context available as 'sc' (master = local[*], app id = local-1652767432473).
Spark session available as 'spark'.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 3.2.1
      /_/
         
Using Scala version 2.12.15 (OpenJDK 64-Bit Server VM, Java 11.0.15)
Type in expressions to have them evaluated.
Type :help for more information.
```


- 스파크 환경변수 등록

```
vi ~/.bash_profile


if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin

#SPARK HOME 등록
export SPARK_HOME=$HOME/sparkㅑ

#PATH 환경변수에 $SPARK_HOME 추가
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin

#alias를 통해 spark/pyspark 명령어 등록
alias spark="$SPARK_HOME/bin/spark-shell"
alias pyspark="$SPARK_HOME/bin/pyspark"
--------------------------------------------------------------------------

# 변경사항 적용하기
$ source ~/.bash_profile
```

- spark 실행

```
ithingvvv@instance-1:~/spark/bin$ spark
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.spark.unsafe.Platform (file:/home/ithingvvv/spark/jars/spark-unsafe_2.12-3.2.1.jar) to constructor java.nio.DirectByteBuffer(long,int)
WARNING: Please consider reporting this to the maintainers of org.apache.spark.unsafe.Platform
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
22/05/17 06:09:50 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Spark context Web UI available at http://instance-1.us-west4-b.c.avid-stone-347506.internal:4040
Spark context available as 'sc' (master = local[*], app id = local-1652767792234).
Spark session available as 'spark'.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 3.2.1
      /_/
         
Using Scala version 2.12.15 (OpenJDK 64-Bit Server VM, Java 11.0.15)
Type in expressions to have them evaluated.
Type :help for more information.

scala> 
```

```
pyspark 실행

ithingvvv@instance-1:~/spark/bin$ pyspark
Python 3.7.3 (default, Jan 22 2021, 20:04:44) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.spark.unsafe.Platform (file:/home/ithingvvv/spark/jars/spark-unsafe_2.12-3.2.1.jar) to constructor java.nio.DirectByteBuffer(long,int)
WARNING: Please consider reporting this to the maintainers of org.apache.spark.unsafe.Platform
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
22/05/17 06:10:28 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 3.2.1
      /_/

Using Python version 3.7.3 (default, Jan 22 2021 20:04:44)
Spark context Web UI available at http://instance-1.us-west4-b.c.avid-stone-347506.internal:4040
Spark context available as 'sc' (master = local[*], app id = local-1652767830340).
SparkSession available as 'spark'.
>>> 


```

