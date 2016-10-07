This page has migrated to https://wilsonmar.github.io/puppet

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

 For example, the command to install an Apache web server on Ubuntu:

```
sudo apt-get install apache2
```

On Redhat:

```
sudo yum install httpd
```

Note the different providers (apt vs. yum).

## <a name="Manifests"> Manifests</a>
Manifest files are stored by default in folder 

  <strong>etc/puppet/manifests/site.pp</strong> (pp = public program).
  
`etc/puppet` is the value of default <strong>$confdir</strong>.


## <a name="DirectoryEnv"> Directory Environments</a>
Alternately, several enviornments (dev, test, prod) 
can be setup with directory enviornments stored in different folders,
defined in:

    <strong>etc/puppet/puppet.conf</strong>

It contains sections: [master], [agent], and [main] (if master and agent are not setup):

  * logdir = /var/log/puppet
  * rundir = /var/run/puppet
  * ssldir = $vardir/ssl

The default environmenttimeout is 5 minutes when a server is checked for changes.


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


 
