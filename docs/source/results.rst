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
