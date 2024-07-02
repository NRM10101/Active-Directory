# Active-Directory

Active Directory (AD) is a directory service developed by Microsoft for Windows domain networks. It is used for managing permissions and access to network resources. AD stores data as objects, including users, groups, and devices, and organizes them into a hierarchical structure. Key features include:

Centralized Management: Provides a single point of management for network resources.
Authentication and Authorization: Manages user login and access permissions.
Group Policy: Allows administrators to implement specific configurations for users and computers.
Scalability: Can be used in small or large-scale environments.
Integration: Works with other Microsoft services and applications.
AD helps in streamlining IT administration and enhancing security by ensuring that only authorized users have access to resources.

![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d16042fc-e773-4e71-aee2-8bd4c55d1c75)

# Insatall Splunk and Sysmon

## Install Splunk Universal Folder in Target Machine and Our Server

Target Machine
1. Changed the hostname as Target-PC
2. Assign static IPV4 address for the target machine
   
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/419b350b-a15b-4016-8074-7984c21b3688)

Accessing Splunk server

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d7fb7fa2-aa41-4aae-aa1e-3f0c52403b72)

   Now goto www.splunk.com and login using your splunk account
   And download the Splunk universal Folder and install it
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/198589e7-ea6a-442c-8a19-886f9ffb8597)

### Now download the Sysmon
   Sysmon (System Monitor) is a Windows service and driver that logs detailed system activity to the event log. It tracks process creations, network connections, and changes to file creation times, helping to detect and investigate malicious activity. It's part of the Sysinternals suite and is used for advanced monitoring and forensic analysis.

   Sysmon configuration we use  https://github.com/olafhartong/sysmon-modular Download sysmonconfig.xml
   Now install the sysmon with downloaded configuration file

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/6587b4fb-a91f-4a8d-b3fd-293f2659c550)

   Now we need to instruct our splunk forwarder on what we want to send over to our Splunk Server
   To do this we must configure a file called inputs.conf
   For this we use inputs.conf file from github
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/31c395a3-e13f-46ac-80db-944dcc47caa8)

   And change Splunk Forwarder Logon as Local System as follows

   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/00203270-885a-4042-af59-f3a403c91cf0)

   And restart the service

   Now we have Sysmon installed and Universal forwarder installed along with updated inputs.conf

   Login to Splunk Server 
   ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/f8d7bad6-3118-41e0-a27a-5484914a8712)

   Create index named endpoint
   Now we should make sure that splunk server to recieve data
   >Forwarding and Receiving
    ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/05c1682a-16ee-4175-98e0-3f9ed9bf9aab)

  If we everything setup correctly we should data comming from our target machine

  ![image](https://github.com/NRM10101/Active-Directory-/assets/126091408/d9fb2454-36ec-4058-a158-6089bc1273f6)




   

   


   

