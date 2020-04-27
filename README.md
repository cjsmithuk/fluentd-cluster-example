# Simple container / concentrator fluentd architcture test case

## Two process fluentd environment:

 * container instance -> per node (k8s/physical).
	receives messages via syslog
	receives messages via docker input 
	forwards all messages via fluentd protocol to upstream concentrator cluster (N nodes)
 * concentrator instance -> at least 2 nodes/containers
	receives messages from fluentd protocol
	forwards all messages to splunk
	forwards all messages to ES

## Installation required:

Tested on clean debian 10.3 virtual machine 

apt packages:
	curl, ruby, ruby-dev, gcc, make 

steps to install fluentd:
	# gem install fluentd --no-ri --no-rdoc
	# fluent-gem install fluentd-plugin-splunk-enterprise
		
## To run:

1. Edit splunk token in fluentd-concentrator.conf
2. Run terminal with ./fluentd-concentrator
3. Run terminal with ./fluentd-containerengine
4. Run ./sendlog to send a message to the container engine syslog
	
