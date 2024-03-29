# pfsense-syslog-ng
syslog-ng parser for pfsense logs that can run on a Raspberry Pi 4 (Ubuntu 22 tested) and probably any x86/x64 distro as well.

THERE IS NO GUARANTEE THAT I AM PARSING CORRECTLY. I usually get at least one field wrong, and will correct after I notice.

Basic syslog-ng patterndb parser for syslog-ng. Tested using pfsense 2.7.2-RELEASE and syslog-ng 3.35.1 on (separate machine) Ubuntu-Arch on RasPi. It should definitely run on syslog-ng 4+, but I can't get it to compile for Ubuntu Arch/RasPi yet. 
pfsense set to syslog (RFC 5424, with RFC 3339 microsecond-precision timestamp.)

pfsense.conf -- set port as required. pfsense appears to do udp only. Since it can run on RasPi, you can always deploy one next to your remote pfsense and then have syslog-ng relay using TLS.

pfense.xml -- patterndb file for pfsense to pull fields out of log lines. Firewall events only, IPv4 only so far.

logtash/pfsense.conf -- basic logstash file to send parsed log to elastic. Can be easily modified to send to kafka or any other of the logstash output plugins.

Why not do parsing in Logstash? Logstash can do a lot of parsing, and it's probably easier to write if more verbose, but syslog-ng does it more efficiently. Syslog-ng and logstash are both running on a RasPi 4 with 8GB of ram. Parsing in syslog-ng generally scales better than logstash, but that's just my opinion.
