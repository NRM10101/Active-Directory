# Active-Directory

Active Directory (AD) is a directory service developed by Microsoft for Windows domain networks. It is used for managing permissions and access to network resources. AD stores data as objects, including users, groups, and devices, and organizes them into a hierarchical structure. Key features include:

Centralized Management: Provides a single point of management for network resources.

Authentication and Authorization: Manages user login and access permissions.

Group Policy: Allows administrators to implement specific configurations for users and computers.

Scalability: Can be used in small or large-scale environments.

Integration: Works with other Microsoft services and applications.

AD helps in streamlining IT administration and enhancing security by ensuring that only authorized users have access to resources.

![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d16042fc-e773-4e71-aee2-8bd4c55d1c75)

# Install Splunk and Sysmon

### Splunk Universal Forwarder
The Splunk Universal Forwarder is a lightweight version of Splunk designed to collect and forward log data to a Splunk instance (like Splunk Enterprise or Splunk Cloud) for indexing and analysis. It is optimized for performance and efficiency, with minimal impact on the host system. Key features include:

1. **Data Collection:** Gathers log data from various sources, including files, directories, and network ports.
2. **Data Forwarding:** Sends collected data to a central Splunk server for processing and indexing.
3. **Lightweight:** Designed to be resource-efficient, making it suitable for deployment on numerous endpoints.
4. **Security:** Ensures secure data transmission using encryption.

### Sysmon (System Monitor)
Sysmon is a Windows system service and driver that logs detailed system activity to the Windows event log. It is part of the Sysinternals suite and is commonly used for advanced system monitoring and forensic analysis. Key features include:

1. **Process Creation Logging:** Records details about new processes, including command line arguments and executable hashes.
2. **Network Connection Logging:** Logs TCP and UDP network connections.
3. **File Creation Time Changes:** Monitors and logs changes to file creation times to detect tampering.
4. **Registry Event Logging:** Tracks changes to the Windows Registry.
5. **Event Tagging:** Tags events with unique identifiers for easier correlation and analysis.

### Integration of Splunk Universal Forwarder and Sysmon
Sysmon generates detailed logs about system activity, which can be collected and forwarded by the Splunk Universal Forwarder to a Splunk server. This integration allows for advanced monitoring, analysis, and visualization of security-related events, helping organizations to detect and respond to potential threats more effectively.

## Install Splunk Universal Folder in Target Machine and Our Server
![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/b21e8011-0428-4421-b5d4-6e508cb0d579)


## Target Machine
1. Changed the hostname as Target-PC
2. Assign static IPV4 address for the target machine
   
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/419b350b-a15b-4016-8074-7984c21b3688)


3. Now goto www.splunk.com and login using your splunk account
   And download the Splunk universal Folder and install it
   
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/198589e7-ea6a-442c-8a19-886f9ffb8597)

5. Now download the Sysmon
   
   Sysmon (System Monitor) is a Windows service and driver that logs detailed system activity to the event log. It tracks process creations, network connections, and changes to file creation times, helping to detect and investigate malicious activity. It's part of the Sysinternals suite and is used for advanced monitoring and forensic analysis.

   Sysmon configuration we use  https://github.com/olafhartong/sysmon-modular
   
   Download sysmonconfig.xml
   
   Now install the sysmon with downloaded configuration file

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/6587b4fb-a91f-4a8d-b3fd-293f2659c550)

   Now we need to instruct our splunk forwarder on what we want to send over to our Splunk Server.
   
   To do this we must configure a file called inputs.conf
   
   For this we use inputs.conf file from github
   
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/31c395a3-e13f-46ac-80db-944dcc47caa8)

   And change Splunk Forwarder Logon as Local System as follows

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/00203270-885a-4042-af59-f3a403c91cf0)

   And restart the service

   Now we have Sysmon installed and Universal forwarder installed along with updated inputs.conf

   Accessing Splunk server

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d7fb7fa2-aa41-4aae-aa1e-3f0c52403b72)

   Login to Splunk Server
   
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/f8d7bad6-3118-41e0-a27a-5484914a8712)

   Create index named endpoint
   
   Now we should make sure that splunk server to recieve data
   
   >Forwarding and Receiving
   
    ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/05c1682a-16ee-4175-98e0-3f9ed9bf9aab)

  If we everything setup correctly we should data comming from our target machine

  ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d9fb2454-36ec-4058-a158-6089bc1273f6)

## Active Directory(Windows Server)

1. Chnage the hostname as ActiveDirectory
2. Assign the static IPv4 address as 192.168.10.7
3. Download the Splunk universal folder & install it
4. Download Sysmon on our windows server
   Sysmon configuration we use  https://github.com/olafhartong/sysmon-modular 
   Download sysmonconfig.xml
   Now install the sysmon with downloaded configuration file
   
   Now we need to instruct our splunk forwarder on what we want to send over to our Splunk Server
   To do this we must configure a file called inputs.conf
   For this we use inputs.conf file from github
   
![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/e752d5ea-9adc-4e0e-90ce-38925954e437)

   
   Anytime you update inputs.conf file you must restart splunk universal folder service

Finally now you have Integrated of Splunk Universal Forwarder and Sysmon on Windows Server and Target machine...

   



   


   

