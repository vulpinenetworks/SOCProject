Technologies Used
====

Cisco ASA
------------

We chose to implement the Cisco ASA-V-5 Virtual Security Appliance.

Method
^^^^^^
- Of its well-established presence in the IT Security Industry and for ease of configuration and Maintenace as well as support.
- The ASA has a vast array of built-in security measures such as ACL’s, Threat Detection, Scanning and Botnet filtering.



Cisco Umbrella DNS
------------

We chose to implement the Cisco Umbrella DNS.

Method
^^^^^^
- In addition to the ASA, we implemented network wide Cisco Umbrella (OpenDNS) DNS to detect malicious activity at the source on our network.
- Umbrella also was chosen to ensure end-user compliance on our network by restricting access to timewasting and adult sites.
- Umbrella further selected due to its ability to block systems such as DNSVPN and Crypto-mining Applications.

Splunk
------------

We chose to implement Splunk.

Method
^^^^^^
- Of its wide array of supported systems and flexibility to log any structure or source with a wide array of methods.
- Splunk has been proven to lower companies risks of data breaches and fraud due to its complex searching and visualization platform.
- Umbrella further selected due to its ability to block systems such as DNSVPN and Crypto-mining Applications.
- Splunk hooked in to rsyslog and AWS to provide logging on various network datapoints.

Amazon Web Services
------------

We chose to implement AWS.

Method
^^^^^^
- Amazon Web Services was chosen due to its logging integration with Cisco Umbrella which was then forwarded to our syslog server by a custom written script to send the data to Splunk.
