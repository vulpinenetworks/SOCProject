Syslog Server Setup
====
#. We installed rsyslog using yum and edited the config file to listen on TCP 514
#. Then using cockpit we allowed syslog traffic thru the firewall
#. We then tested that rsyslog is getting console output from the ASA

   .. image:: img\syslogasa.png
#. Once confirmed that rsyslog was working with the output below we had to install the splunk universal forwarder.
#. We obtained the rpm image using wget from the splunk website to download the rpm installer
   
   .. image:: img\splunkfrpm.png
#. We ran the rpm installer to install the forwarder
#. We then added the splunk server with the forwarder by running the command add-forward-server ipaddress
#. We then verified that Splunk Forwarder sees our Splunk Server
  
  .. image:: img\splunkforward.png

