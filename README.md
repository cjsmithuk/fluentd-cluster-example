# Simple container / concentrator fluentd architcture test case

## Architecture overview

* container instance -> per node (k8s/physical).
  * receives messages via syslog
  * receives messages via docker input 
  * forwards all messages via fluentd protocol to upstream concentrator cluster (N nodes)
* concentrator instance -> at least 2 nodes/containers
  * receives messages from fluentd protocol
  * forwards all messages to splunk
  * forwards all messages to ES

## Installation

Tested on clean debian 10.3 virtual machine 

1. `# apt install curl ruby ruby-dev gcc make`
2. `# gem install fluentd --no-ri --no-rdoc`
3. `# fluent-gem install fluentd-plugin-splunk-enterprise`
		
## Runtime

1. Edit splunk token and host in `fluentd-concentrator.conf`
2. Open terminal with `./fluentd-concentrator`
3. Open terminal with `./fluentd-containerengine`
4. Run `./sendlog` to send a message to the container engine syslog
	
