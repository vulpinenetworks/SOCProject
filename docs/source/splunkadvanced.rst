Splunk Searching and Dashboards
====
This section of our documentation outlines the steps and processes taken to setup our Splunk Instance to search and dashboard various datapoints on our network.

1. The first step we took was insuring that splunk can search data and that output was returned.
 .. code-block:: bash

   host="_gateway"
   host="umbrelladns"
   
2. Once all datapoints were verified a dashboard was created under the Search App and titled "SOC" for Security Operations Center. All datapoints follow a standard layout of 
Data and then a Log View.

3.The first datapoint we logged was failed attempts to login to the routers local AAA database. This is used for ASDM and WEBVPN access to measure possible brute force attacks, we used the following searches.

 .. code-block:: bash

   host="_gateway" authentication: rejected | stats sum(linecount) as total
   host="_gateway" authentication: rejected

 The first query sums all the records that match "Authentication Rejected" and the second one displays a events log of the search results.
 
 .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/AuthError.png

 4 .The next datapoint we logged was ACL Deny events, this would allow a SOC Engineer high visibility in to actions on the network which are hitting a deny rule on the firewall.

 .. code-block:: bash

   host="_gateway" access-list deny | stats sum(linecount) as total
   host="_gateway" access-list deny

 The first query sums all the records that match "access-list deny" and the second one displays a events log of the search results.
 
 .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/ACLDeny.png

5 .The next datapoint we logged was amount of times locked out accounts have been attempted to be accessed, this is also usefull to Engineers to detect a brute force attempt.

 .. code-block:: bash

   host="_gateway" Internal Error | stats sum(linecount) as total
   host="_gateway" Internal Error

 The first query sums all the records that match "Internal Error" and the second one displays a events log of the search results.
 
 .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/SSHLockedOut.png


7 .The next datapoint we logged was BotNet Traffic, this filter allows us to see identified Botnet Traffic.

 .. code-block:: bash
 
   host="_gateway" blacklist | stats sum(linecount) as total
   host="_gateway"

 The first query searches for text sums all the records that match and then saves it as a variable, and then graphs it, the second search sums all DNS events and the third search displays a events log of the search results.
 
 .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/Botnet.png




7 .The next datapoint we logged was DNS Traffic, we logged all traffic and reported a graph for Allowed Vs Blocked, Total Traffic and a Events Log.

 .. code-block:: bash

   host="umbrelladns"  | eval pass=mvfilter(match(Allowed,"Allowed")) | eval fail= mvfilter(match(Allowed, "Blocked")) | streamstats count(pass) as success, count(fail) as no |    chart count by no
   host="_umbrelladns" | stats sum(linecount) as total
   host="umbrelladns"

 The first query searches for text sums all the records that match and then saves it as a variable, and then graphs it, the second search sums all DNS events and the third search displays a events log of the search results.
 
 .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/dns.png

