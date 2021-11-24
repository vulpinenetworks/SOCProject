.. container::

Cisco ASA-V Install Steps
====




#. The first step we took in setting up our Cisco ASAv is assigning the administrator interface a static IP address to do this we accessed the direct console of the ASAv and issued the following commands (seen below)
#. Once the commands were issued and DHCP was enabled we were able to switch to the Admin workstation and connect to the ASA’s internal webserver to download the ASDM Utility.

   .. image:: https://vulpinenetworkscdn.s3.ca-central-1.amazonaws.com/ASDM.png?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEIz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJGMEQCICk4PTlfPbX7YcZuuWDwjYHpODZQIFMeeaLdroFVFEW7AiAEPGX9vk7fDU638XuBul%2B6wSOBY0B40aycur2jCGlKsCr2AghUEAIaDDc3MjIyNTk1MjQyMSIMx%2BO8V23dbpnnOiE8KtMCivZb0nd4L1H6ZkLFIs7VdjUFsQ2dWlWPNhg4AzWwGBcf8A6zwQPDrzqUpHpqMIW01MUqE9Mz609krbsRedtYeNADSQuOMST3EEOLneN2RwWbPM8OHfl4tJxh%2B8dT%2B9KPOVYdOL9tXhbRv9c%2FOYaeyI8Yov7cI77DijiWs5Z3lWBuWykXcXlaNnt2Iggvs1uGNNKhOCsCh%2B%2BCR4CRJ5t1JsOgR9eSH5X6LKfX8TTL7LLfOBKLu4JrBGHfsgmCVf8oZSLMYFiRgix5j6yaxIghOtExrQm6Es5yAPMYtuXKbupBWxVpJiayBjxo0b1B5woZnd2hj1IwkE6SZ%2FSjBv8v0g5frk2cRJ%2BNDDdsgVe1UrDcuU2UXDqKzA9fB818L3vzj3mAMZUWFA1RU0c1ZQs3GH7MoUAwkYbV%2F3mrirEHq%2FJENLSkoB8F0SCmrLODvcbl4lIdMOHd9owGOrQCji7OQE8Afp2NUj%2BRB7GBtd8m8k4BAwdMyU3pfoKxjTQShFbhPvcl8Wi1aF3VlwolkY2tEtqpT1anftMplKjpH8fe6Rsc6ttGExJenYfzLeRphwZuuIOO3WWcnJIseRObOqtMU8KuMiUZb63rh%2BIsDNeI2hBk1OEJC8cCvqKPbnN8BinsfEoisVDOdeDFvFdQVslSvzHeCf5zlbfQK7uVnrfSL18bMplwM53PtXUeYfXfHkvhqr4qgRkdZ1Wl4kaoy1ueeNQUamXUX9Y51Ump7ZVRTjSWpav%2BCr5DvdLd0X1qy8jLJgwF2pcpGh5JlHjMAJqEUjpbCBQ8oH43O35K2Piv%2FTQhn5BvDxoLeac9TFREFSXG3h0vjBUszS5H4jaYCdnNexCglg98KmibVUoZaZUyh7E%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20211124T031848Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIA3HTCA5KSWU2IS5NZ%2F20211124%2Fca-central-1%2Fs3%2Faws4_request&X-Amz-Signature=f61cf35152265e5ca3d9135ee57c0290ee0ac353d5769a3ed5458e4cf1b27aaf
#.  Once the ASDM utility was installed and connection was established to the ASAv, we chose to use the Quick Start Wizard to set up basic Interface settings and other configurationpoints such as NAT and the outside interface.
#. The next step we took in configuration was to set up out Access Lists to control traffic over the network. We chose the following settings.
#. Next we confirmed and fixed any issues with the NAT Rules as well as set up Port Forwarding 
#. Next we enabled and modified the Basic Traffic Inspection on the ASA to allow ICMP and ICMP errors to allow ping traffic through the gateway as this is not allowed by default.
#. Next we enabled Scanning Threat Detection on the ASAv appliance which allows the ASA to monitor traffic and detect activity that is commonly related to attacks such as DDoS or Scanning Attacks.
#.  Next we enabled the botnet traffic filter to allow the ASA to monitor traffic going to known botnet sources and stop identified traffic from reaching its destination. 
#.  Next we setup the ASA to log events higher then Notifications to send log events to the Syslog server. 
#. We then identified the syslog server in the ASA appliance by setting the IP and interface our server sits on.
#. Then as a demo we enabled Cisco WebSSL Clientless VPN on theoutside interface (this was done by using the VPN Wizard)
#. Additional interface’s then had DHCP enabled if applicable
#.  Finally we set the DNS to be resolved by Cisco Umbrella

Cisco ASDM CLI Config Commands
^^^^
.. code-block:: bash

    ASAv(config)# interface gigabitEthernet 0/1
    ASAv(config-if)# nameif Workstation
    ASAv(config-if)# security-level 100
    ASAv(config-if)# ip address 172.16.0.1 255.255.255.0
    ASAv(config)# dhcpd address 172.16.0.10–172.16.0.1 Workstation
    ASAv(config)# dhcpd enable Workstation


