Cisco ASA-V Install Steps
===
.. container::



#. The first step we took in setting up our Cisco ASAv is assigning the administrator interface a static IP address to do this we accessed the direct console of the ASAv and issued the following commands (seen below)
#. Once the commands were issued and DHCP was enabled we were able to switch to the Admin workstation and connect to the ASA’s internal webserver to download the ASDM Utility.
#.  Once the ASDM utility was installed and connection was established to the ASAv, we chose to use the Quick Start Wizard to set up basic Interface settings and other configurationpoints such as NAT and the outside interface.
#. The next step we took in configuration was to set up out Access Lists to control traffic over the network. We chose the following settings.
#. Next we confirmed and fixed any issues with the NAT Rules as well as set up Port Forwarding 
#.  Next we enabled and modified the Basic Traffic Inspection on the ASA to allow ICMP and ICMP errors to allow ping traffic through the gateway as this is not allowed by default.
#. Next we enabled Scanning Threat Detection on the ASAv appliance which allows the ASA to monitor traffic and detect activity that is commonly related to attacks such as DDoS or Scanning Attacks.
#.  Next we enabled the botnet traffic filter to allow the ASA to monitor traffic going to known botnet sources and stop identified traffic from reaching its destination. 
#.  Next we setup the ASA to log events higher then Notifications to send log events to the Syslog server. 
#. We then identified the syslog server in the ASA appliance by setting the IP and interface our server sits on.
#.We then identified the syslog server in the ASA appliance by setting the IP and interface our server sits o
#. Then as a demo we enabled Cisco WebSSL Clientless VPN on theoutside interface (this was done by using the VPN Wizard)
#. Additional interface’s then had DHCP enabled if applicable
#.  Finally we set the DNS to be resolved by Cisco Umbrella

.. container::
Cisco ASA-V Management Interface ASDM CLI Code
-------------
.. code-block:: console

    ASAv(config)# interface gigabitEthernet 0/1
    ASAv(config-if)# nameif Workstation
    ASAv(config-if)# security-level 100
    ASAv(config-if)# ip address 172.16.0.1 255.255.255.0
    ASAv(config)# dhcpd address 172.16.0.10–172.16.0.1 Workstation
    ASAv(config)# dhcpd enable Workstation

.. container::
