Scan and Attack Results
====

WMAP
----
Wmap quick scans returned no results but then hung when a detailed scan was ran.

DIRB
----
Dirb is a directory scanner that was used in addition to WMAP to find directories, on DVWA it found a total of 6 Directories open to the public.
The open directories are 

- Config
- Docs
- External
    - Favicon
    - Index
    - Php.ini 
    - phpinfo
    - robots
    - serverstatus
This scan showed two files that would be of intrest to a malicious actor due to their nature of configuration, those would be php.ini and phpinfo
To run DIRB we ran the following command
  
.. code-block:: console

    dirb http://10.180.110.250
   
   
Skipfish
----
Skipfish is an alternitive web vuln scanning system, on DVWA it found a many open vulns.
You can view the results below:

- [Internal warning] 	Response varies randomly, skipping checks (5)
- [Internal warning] 	Resource fetch failed (50)
- [Informational note] 	Incorrect or missing charset (low risk) (6)
- [Informational note] 	Incorrect or missing MIME type (low risk) (1)
- [Informational note] 	Password entry form - consider brute-force (2)
- [Informational note] 	Directory listing enabled (10)
- [Informational note] 	Server error triggered (2)
- [Informational note] 	Resource not directly accessible (2)
- [Informational note] 	New 404 signature seen (1)
- [Informational note] 	New 'Server' header value seen (1)
- [Informational note] 	New HTTP cookie added (2)
 
.. code-block:: console

    skipfish -o scan http://10.180.110.250


Windows Custom Script 
----

- All pings that are denied on ACL were dropped
- All DNS policy violations were blocked
- Malware file was blocked by firewall

Kali Custom Script 
----
- Hydra returned one result for a SSH password
- Hydra could not crack the VPN password
- NMAP was not successfull
- Remote SSH to webserver was successfull
- WMAP Failed (see above)
