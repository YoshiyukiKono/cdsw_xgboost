# XGBoost (on CDSW)


## Data Preparation
```
wget https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv
hdfs dfs -put iris.csv /tmp/.
```

## How to use
Run (All) SparkMLlibPipeline_simplified.scala

## Compile
NOT DEPENDS - I switched to use spark.jar.packages in spark-defaults.conf.
### Maven Setup
```
wget http://mirrors.ocf.berkeley.edu/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz
tar xzvf apache-maven-3.6.1-bin.tar.gz 
export PATH=$PATH:/home/cdsw/apache-maven-3.6.1/bin
```

### XGBoost Compile
```
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
mkdir build
cd build
cmake ..
make -j4

cd /home/cdsw/xgboost/jvm-packages
mvn package
```

or

https://medium.com/@bogdan.cojocar/how-to-make-xgboost-available-in-the-spark-notebook-de14e425c948

```
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
make -j4

cd /home/cdsw/xgboost/jvm-packages
mvn -DskipTests install
```
Note: You may fail with poor resources, e.g. 2GB memory. I succeeded to finish with 4GB memory.

```
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for XGBoost JVM Package 1.0.0-SNAPSHOT:
[INFO] 
[INFO] XGBoost JVM Package ................................ SUCCESS [  2.429 s]
[INFO] xgboost4j_2.12 ..................................... SUCCESS [01:26 min]
[INFO] xgboost4j-spark_2.12 ............................... SUCCESS [02:04 min]
[INFO] xgboost4j-flink_2.12 ............................... SUCCESS [ 36.884 s]
[INFO] xgboost4j-example_2.12 ............................. SUCCESS [  7.665 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  04:18 min
[INFO] Finished at: 2019-11-08T04:31:50Z
[INFO] ------------------------------------------------------------------------
```
