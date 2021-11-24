Cisco Umbrella DNS Setup
====
1. Create a trial on umbrella.cisco.com
2. Pointed network DNS to umbrella network and verified connection.
3. We then set up basic rules to allow traffic to pass or be blocked at the DNS level.
  .. image:: img/block1.png

  .. image:: img/block2.png

4. Then we tested that the DNS filtering is successful. 

  .. image:: img/testblock.png

  .. image:: img/testblock2.png

  .. image:: img/testblock3.png

5. Then we set up Umbrella to log in to a Cisco Owned AWS S3 Bucket which will then be pulled down and fed into Splunk 

  .. image:: img/s3.png
 
****
Umbrella to AWS S3 Bucket to Log File to Splunk Server
****

1. After setting up Umbrella to Forward to AWS:S3 and then obtaining our login credentials we installed the AWS CLI utility from aws.com and installed it using wget.

  .. code-block:: bash
  
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install


2. After setting up Umbrella to Forward to AWS:S3 and then obtaining our login credentials we installed the AWS CLI utility from aws.com and installed it using wget.

  .. code-block:: bash
  
    aws config
    
3. We then wrote a script to autommatically pull the files down from the s3 bucket

  .. code-block:: bash
  
    #!/bin/bash
    cd /TESTDIR/
    echo "Working" >> /TESTDIR/file
    aws s3 sync s3://cisco-managed-ca-central-1/s3://cisco-managed-ca-central-1/7940666_50c08cffa1c94843903ff686e0b70afc19799fe5 /TESTDIR/
      
4. We then wrote a script to autommatically pull the files down from the s3 bucket

  .. code-block:: bash
  
    */5 * * * /home/student02/test >> /TESTDIR/cronhasrun5
    
    
5.	Then we set up a source in splunk to the directory of the logs from umbrella. 

  .. image:: img/umbsource.png
  
