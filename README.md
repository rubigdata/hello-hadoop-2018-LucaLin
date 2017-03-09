# hello-hadoop
Initialization repo for assignment 2

First look at the assignment!
https://rubigdata.github.io/course/assignments/A2-mapreduce.html


Useful history of commands:

    export PATH=${JAVA_HOME}/bin:${PATH}
    export HADOOP_CLASSPATH=${JAVA_HOME}/lib/tools.jar
    bin/hadoop com.sun.tools.javac.Main /mnt/bigdata/hello-hadoop/WordCount.java

    pushd /mnt/bigdata/hello-hadoop
    jar cf wc.jar WordCount*.class
    popd

    bin/hdfs dfs -mkdir /user/root/input
    bin/hadoop jar /mnt/bigdata/hello-hadoop/wc.jar WordCount /user/root/input /user/root/output
    bin/hadoop fs -ls output

