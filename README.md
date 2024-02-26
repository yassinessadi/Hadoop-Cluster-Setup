### **Hadoop Cluster Setup**

<img src="assets/Animation.gif" alt="hadoop-cluster-setup" />

<hr />

### **Road Map**
<img src="assets/big data - bd.png">

### **Prerequisites**
- Java.
- Download a stable version of Hadoop from Apache mirrors.
- red hat linux system or any linux distro.
- Oracle VM VirtualBox


### **Installation**
Installing a Hadoop cluster typically involves unpacking the software on all the machines in the cluster or installing it via a packaging system as appropriate for your operating system. It is important to divide up the hardware into functions.

Typically one machine in the cluster is designated as the NameNode and another machine as the ResourceManager, exclusively. These are the masters. Other services (such as Web App Proxy Server and MapReduce Job History server) are usually run either on dedicated hardware or on shared infrastructure, depending upon the load.

The rest of the machines in the cluster act as both DataNode and NodeManager. These are the workers.


### **Networking**
#### **`Oracle VM VirtualBox`**
Tools > Preferences ( icon ) > Network, and then double-click the appropriate NAT Network.

1. Select the NAT network option in VirtualBox.
2. Create a new NAT network if one doesn't exist already.
3. Configure the network with the following example IP address: `192.168.7.0`.
4. Enable DHCP for the network.
5. Click on "Apply" to save the changes.

<img src="assets/Nat network.png" />

#### **`redhad:`**

```bash
sudo vi hosts
```
Add this host with the API to the hosts file.
```bash
192.168.7.4 namenode1
192.168.7.6 datanode1
192.168.7.7 datanode2
```


### **Configuring Hadoop in Non-Secure Mode**
Hadoop’s Java configuration is driven by two types of important configuration files:

- Read-only default configuration - core-default.xml, hdfs-default.xml, yarn-default.xml and mapred-default.xml.

- Site-specific configuration - etc/hadoop/core-site.xml, etc/hadoop/hdfs-site.xml, etc/hadoop/yarn-site.xml and etc/hadoop/mapred-site.xml.

To configure the Hadoop cluster you will need to configure the environment in which the Hadoop daemons execute as well as the configuration parameters for the Hadoop daemons.

#### **`Configure The Environment`:**
First, make sure you have installed Vim on your system. For example, in Red Hat :
```bash
sudo dnf search vim
```


```bash
sudo vi ~/.bashrc
```
Then add these arguments to the .bashrc file.
```bash
# java
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk
export PATH=$JAVA_HOME/bin:$PATH
# hadoop
export HADOOP_HOME=/home/jane/hadoop
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_CONF_DIR=${HADOOP_HOME}/etc/hadoop
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export HADOOP_OPTS=-Djava.net.preferIOv4stack=true
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
```



HDFS daemons are NameNode, SecondaryNameNode, and DataNode. YARN daemons are ResourceManager, NodeManager, and WebAppProxy. If MapReduce is to be used, then the MapReduce Job History Server will also be running. For large installations, these are generally running on separate hosts.