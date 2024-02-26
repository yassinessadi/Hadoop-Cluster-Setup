### **Hadoop Cluster Setup**

<img src="assets/Animation.gif" alt="hadoop-cluster-setup" />

<hr />

### **Road Map**
<img src="assets/big data - bd.png">

### **Prerequisites**
- Java.
- Download a stable version of Hadoop from Apache mirrors.
- red hat linux system or any linux distro.


### **Installation**
Installing a Hadoop cluster typically involves unpacking the software on all the machines in the cluster or installing it via a packaging system as appropriate for your operating system. It is important to divide up the hardware into functions.

Typically one machine in the cluster is designated as the NameNode and another machine as the ResourceManager, exclusively. These are the masters. Other services (such as Web App Proxy Server and MapReduce Job History server) are usually run either on dedicated hardware or on shared infrastructure, depending upon the load.

The rest of the machines in the cluster act as both DataNode and NodeManager. These are the workers.
