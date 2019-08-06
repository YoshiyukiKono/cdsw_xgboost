# XGBoost (on CDSW)

## Maven Setup
```
wget http://mirrors.ocf.berkeley.edu/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz
tar xzvf apache-maven-3.6.1-bin.tar.gz 
export PATH=$PATH:/home/cdsw/apache-maven-3.6.1/bin
```

## XGBoost Compile
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
## Sample Data Download
```
wget https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv
hdfs dfs -put iris.csv /tmp/.
```
