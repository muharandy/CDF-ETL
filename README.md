# CDF-ETL

Exploring NiFi for Batch ETL. Summary

- Staging Table creation using Hive via Hue
- Initial load with NiFi with QueryDatabaseTable, ConvertRecord with AvroReader and CSVRecordSetWriter, followed by PutHDFS
- Data Profiling and Exploration with CDSW
- Data transformation or aggregation using PySpark invoked via ExecuteSparkInteractive through Livy

## Install CDH + CDF + CDSW

Install using Fabio's OneNodeCDHCluster:
- https://github.com/fabiog1901/OneNodeCDHCluster

## Install Livy

Download and Install Livy
```
wget https://www.apache.org/dyn/closer.lua/incubator/livy/0.6.0-incubating/apache-livy-0.6.0-incubating-bin.zip
unzip apache-livy-0.6.0-incubating-bin.zip
cd apache-livy-0.6.0-incubating-bin
export SPARK_HOME=/opt/cloudera/parcels/CDH/lib/spark
export HADOOP_CONF_DIR=/etc/hadoop/conf
sudo ln -s /etc/hive/conf/hive-site.xml $SPARK_HOME/conf
```

Edit livy.conf to enable HiveContext
```
cp $LIVY_HOME/conf/livy.conf.template $LIVY_HOME/conf/livy.conf
vi $LIVY_HOME/conf/livy.conf
```

Set the following config to `true`
```
livy.repl.enable-hive-context = true
```

Start Livy
```
./$LIVY_HOME/bin/livy-server start
```
