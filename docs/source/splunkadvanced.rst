Splunk Searching and Dashboards
^^^^
This section of our documentation outlines the steps and processes taken to setup our Splunk Instance to search and dashboard various datapoints on our network.

1. The first step we took was insuring that splunk can search data and that output was returned.
 .. code-block:: bash

   host="_gateway"
   host="umbrelladns"
   
2. Once all datapoints were verified a dashboard was created under the Search App and titled "SOC" for Security Operations Center. All datapoints follow a standard layout of 
Data and then a Log View.

3. The first datapoint we logged was failed attempts to login to the routers local AAA database. This is used for ASDM and WEBVPN access to measure possible brute force attacks, we used the following searches.
 .. code-block:: bash

   host="_gateway" authentication: rejected | stats sum(linecount) as total
   host="_gateway" authentication: rejected
The first query sums all the records that match "Authentication Rejected" and the second one displays a events log of the search results.

 
