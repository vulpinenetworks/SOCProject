.. container::

   1. The first step we took in setting up our Cisco ASAv is assigning
      the administrator interface a static IP address to do this we
      accessed the direct console of the ASAv and issued the following
      commands
.. code-block:: console

    ASAv(config)# interface gigabitEthernet 0/1
    ASAv(config-if)# nameif Workstation
    ASAv(config-if)# security-level 100
    ASAv(config-if)# ip address 172.16.0.1 255.255.255.0
    ASAv(config)# dhcpd address 172.16.0.10–172.16.0.1 Workstation
    ASAv(config)# dhcpd enable Workstation

.. container::

   #. Once the commands were issued and DHCP was enabled we were able to
      switch to the Admin workstation and connect to the ASA’s internal
      webserver to download the ASDM Utility.



   #.  Once the ASDM utility was installed and connection was
         established to the ASAv, we chose to use the Quick Start Wizard
         to set up basic Interface settings and other configuration
         points such as NAT and the outside interface.


   #. The next step we took in configuration was to set up out Access
         Lists to control traffic over the network. We chose the
         following settings.
