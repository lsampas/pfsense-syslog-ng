# pfsense-syslog-ng
syslog-ng parser for pfsense logs

Basic syslog-ng patterndb parser for syslog-ng. Tested using pfsense 2.7.2-RELEASE and  syslog-ng 3.35.1 on (separate machine) Ubuntu-Arch on RasPi.
pfsense set to syslog (RFC 5424, with RFC 3339 microsecond-precision timestamp.)

pfsense.conf -- set port as required. pfsense appears to do udp only. Since it can run on RasPi, you can always deploy one next to your remote pfsense and then have syslog-ng relay using TLS.

pfense.xml -- patterndb file for pfsense to pull fields out of log lines. Firewall events only, IPv4 only so far.
