<!--
Copyright (c) 2010 Yahoo! Inc., 2012 - 2016 YCSB contributors.
All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you
may not use this file except in compliance with the License. You
may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied. See the License for the specific language governing
permissions and limitations under the License. See accompanying
LICENSE file.
-->

Yahoo! Cloud System Benchmark (YCSB)
====================================
[![Build Status](https://travis-ci.org/brianfrankcooper/YCSB.png?branch=master)](https://travis-ci.org/brianfrankcooper/YCSB)

Links
-----
http://wiki.github.com/brianfrankcooper/YCSB/  
https://labs.yahoo.com/news/yahoo-cloud-serving-benchmark/
ycsb-users@yahoogroups.com  

Getting Started
---------------

1. Download the [latest release of YCSB](https://github.com/brianfrankcooper/YCSB/releases/latest):

    ```sh
    curl -O --location https://github.com/brianfrankcooper/YCSB/releases/download/0.11.0/ycsb-0.11.0.tar.gz
    tar xfvz ycsb-0.11.0.tar.gz
    cd ycsb-0.11.0
    ```
    
2. Set up a database to benchmark. There is a README file under each binding 
   directory.

3. Run YCSB command. 

    On Linux:
    ```sh
    bin/ycsb.sh load basic -P workloads/workloada
    bin/ycsb.sh run basic -P workloads/workloada
    ```

    On Windows:
    ```bat
    bin/ycsb.bat load basic -P workloads\workloada
    bin/ycsb.bat run basic -P workloads\workloada
    ```

  Running the `ycsb` command without any argument will print the usage. 
   
  See https://github.com/brianfrankcooper/YCSB/wiki/Running-a-Workload
  for a detailed documentation on how to run a workload.

  See https://github.com/brianfrankcooper/YCSB/wiki/Core-Properties for 
  the list of available workload properties.

Building from source
--------------------

YCSB requires the use of Maven 3; if you use Maven 2, you may see [errors
such as these](https://github.com/brianfrankcooper/YCSB/issues/406).

To build the full distribution, with all database bindings:

    mvn clean package

To build a single database binding:

    mvn -pl com.yahoo.ycsb:mongodb-binding -am clean package


Generate Trace
---------------------
```
sudo apt-get install mvn
```
You may need to configure jdk to run mvn.
from follow to get jdk1.8:

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
```
tar -zxvf jdk-8u111-linux-x64.tar.gz 
sudo mkdir /usr/local/java
sudo mv jdk1.8.0_111/ /usr/local/java/
export JAVA_HOME=/usr/local/java/jdk1.8.0_111
export JRE_HOME=/usr/local/java/jdk1.7.0_60/jre
export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
```
Then,configure genTrace.sh

You may only need to alter FILEDIR in genTrace.sh

note that the ```FILEDIR ``` in genTrace.sh means that the location of the trace.
Don't forget last "/" in FILEDIR

run ./genTrace.sh

After run genTrace.h.You need do this:
```
cat workloadu_uniform_run_5000_constant_hashed_1024.trace0 >> workloadu_uniform_load_5000_constant_hashed_1024.trace0 

```
To Concatenate two files to one file.
