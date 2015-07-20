This page provides a quick yet technically deep introduction to Puppet for DevOps automation.

Information here is a combination of several classes I had taken on Puppet:

* <a target="_blank" href="http://www.pluralsight.com/courses/puppet-system-administrators-fundamentals">
  Pluralsight video: Introduction</a> 
  by Ben Piper (@_benpiper) of benpiper.com

MediaWiki which runs PHP reaching MySQL within Ubuntu.


## <a name="Competitors"> Competitors to Puppet</a>
In the configuration management software market:

* SaltStack Enterprise
* Enterprise Chef (requires Ruby skills)
* Ansible 
* CF Engine (first relased 1993)

## <a name="Advantages"> Advantages to Puppet</a>

Puppet is used to automate a way to ensure that all servers have consistent configuration.

Puppet can do this across different versions of different operating systems!
This is possible because Puppet <strong>manifest</strong> files are declarative in that they 
specify the configuration desired (the "what"),
whereas server shell scripts are more complicated since they specify <strong>procedural</strong> (the "how"),
which differ for different operating systems. For example, the command to install an Apache web server on Ubuntu:

```
sudo apt-get install apache2
```

On Redhat:

```
sudo yum install httpd
```

Note the different providers (apt vs. yum);

## <a name="PuppetMaster"> PuppetMaster Server</a>
A PuppetMaster server, a Ruby on Rails app running on Linux (Centos).

Each node runs an agent which can be Unix (BSD and Mac OSX), even Windows.

Nodes connect to the PM over <strong>port 8140</strong>.

The master creates and maintains a catalog of nodes.

The facter collects facts from each node (OS, CPU, network, block devices, etc.).

 
## <a name="Declaration"> Resource Declaration</a>
<strong> Resource declarations</strong> specify each node's
Type (Package, File, or Service) , Title (such as 'ntp'), Attributes/Parameters, Provider:

```
node 'appserver01' {
  package { 'ntp':
    ensure => 'installed';
  }
  file { '/readme.txt':
    ensure  => 'present';
    content => "This file.";
  }
  service { 'ntpd':
    ensure  => 'running';
    enable  => true;
  }
}
```

https://Virtualbox.org/wiki/downloads

https://www.VagrantUp.com/downloads.html

https://github.com/benpiper/puppet-fundamentals-lab


 
