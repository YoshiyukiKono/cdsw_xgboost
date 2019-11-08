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

```
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
make -j4

cd /home/cdsw/xgboost/jvm-packages
mvn package
```
