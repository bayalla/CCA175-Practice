# Flume Basics

## Create a example.conf file

#### example.conf: A single-node Flume configuration
#### Name the components on this agent
a1.sources = r1
a1.sinks = k1
a1.channels = c1
#### Describe/configure the source
a1.sources.r1.type = netcat
a1.sources.r1.bind = localhost
a1.sources.r1.port = 44444
#### Describe the sink
a1.sinks.k1.type = logger
#### Use a channel which buffers events in memory
a1.channels.c1.type = memory
a1.channels.c1.capacity = 1000
a1.channels.c1.transactionCapacity = 100
#### Bind the source and sink to the channel
a1.sources.r1.channels = c1
a1.sinks.k1.channel = c1

## Run the Flume Agent
flume-ng agent --name a1 --conf-file /home/varunu28/example.conf

## Run the web server in another terminal and enter messages
telnet localhost 44444