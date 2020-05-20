## Vagrant Virtual Development Environment for GoLang

###  Install Vagrant ###

* Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* Download and install [Vagrant](http://www.vagrantup.com/downloads.html)

#### Windows Users ####

- Download [Git for Windows](http://msysgit.github.io/):
  - Run the installer and "next" through the wizard until the step to adjust your PATH environment.
  - Choose the third option, "Run Git and included tools from within the Windows Command prompt"
  - **Important**: On the next step, "Configuring the line ending conversions", choose the second option:       "Checkout as-is, commit Unix-style line endings".
  - Choose "next" through any additional steps to complete the Git for Windows install.
  - Open the Windows Command Prompt as **Administrator**
  
##Vagrant - Kafka
Vagrant configuration to setup a partitioned Apache Kafka installation with clustered Apache Zookeeper.
* Three hosts forming a three node Apache Zookeeper Quorum (Replicated ZooKeeper)
* Three Apache Kafka nodes with one broker each

Kafka is installed on all hosts and can be easily accessed through the environment variable ```$KAFKA_HOME```

Here is the mapping of VMs to their private IPs:

| VM Name    | Host Name | IP Address |
| ---------- | --------- | ---------- |
| zookeeper1 | vkc-zk1   | 10.30.3.2  |
| zookeeper2 | vkc-zk2   | 10.30.3.3  |
| zookeeper3 | vkc-zk3   | 10.30.3.4  |
| broker1    | vkc-br1   | 10.30.3.30 |
| broker2    | vkc-br2   | 10.30.3.20 |
| broker3    | vkc-br3   | 10.30.3.10 |

Hosts file entries:

```
10.30.3.2	vkc-zk1
10.30.3.3 	vkc-zk2
10.30.3.4 	vkc-zk3
10.30.3.30 	vkc-br1
10.30.3.20 	vkc-br2
10.30.3.10 	vkc-br3
```

Zookeeper servers bind to port 2181. Kafka brokers bind to port 9092. 



### Connect to the Virtual Machine ###

Start the virtual machine:

     $ vagrant up

Connect to the virtual machine via ssh:

     $ vagrant ssh zookeeper1

Try it out!

     $ cd dev
     $ go run test.go
