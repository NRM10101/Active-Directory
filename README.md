# 🖥️ Active Directory Integration with Splunk and Sysmon

![Active Directory](https://github.com/NRM10101/Active-Directory-/assets/126091408/d16042fc-e773-4e71-aee2-8bd4c55d1c75)

## 🗂️ Overview

**Active Directory (AD)** is a directory service developed by Microsoft for Windows domain networks. It is used for managing permissions and access to network resources. AD stores data as objects, including users, groups, and devices, and organizes them into a hierarchical structure.

### Key Features:
- **Centralized Management**: Provides a single point of management for network resources.
- **Authentication and Authorization**: Manages user login and access permissions.
- **Group Policy**: Allows administrators to implement specific configurations for users and computers.
- **Scalability**: Can be used in small or large-scale environments.
- **Integration**: Works with other Microsoft services and applications.

AD helps in streamlining IT administration and enhancing security by ensuring that only authorized users have access to resources.

---

## 📦 Install Splunk and Sysmon

### 🔧 Splunk Universal Forwarder

The **Splunk Universal Forwarder** is a lightweight version of Splunk designed to collect and forward log data to a Splunk instance (e.g., Splunk Enterprise or Splunk Cloud) for indexing and analysis.

#### Key Features:
1. **📄 Data Collection**: Gathers log data from various sources, including files, directories, and network ports.
2. **🔗 Data Forwarding**: Sends collected data to a central Splunk server for processing and indexing.
3. **⚡ Lightweight**: Designed to be resource-efficient, making it suitable for deployment on numerous endpoints.
4. **🔐 Security**: Ensures secure data transmission using encryption.

---

### 👀 Sysmon (System Monitor)

**Sysmon** is a Windows system service and driver that logs detailed system activity to the Windows event log. It is part of the Sysinternals suite and is commonly used for advanced system monitoring and forensic analysis.

#### Key Features:
1. **📑 Process Creation Logging**: Records details about new processes, including command-line arguments and executable hashes.
2. **🌐 Network Connection Logging**: Logs TCP and UDP network connections.
3. **📝 File Creation Time Changes**: Monitors and logs changes to file creation times to detect tampering.
4. **🛠️ Registry Event Logging**: Tracks changes to the Windows Registry.
5. **🏷️ Event Tagging**: Tags events with unique identifiers for easier correlation and analysis.

---

### 🔄 Integration of Splunk Universal Forwarder and Sysmon

**Sysmon** generates detailed logs about system activity, which can be collected and forwarded by the **Splunk Universal Forwarder** to a Splunk server. This integration allows for advanced monitoring, analysis, and visualization of security-related events, helping organizations detect and respond to potential threats more effectively.

---

## ⚙️ Installation Steps

### 🖥️ Install Splunk Universal Forwarder on Target Machine and Server

![Splunk Installation](https://github.com/NRM10101/Active-Directory-/assets/126091408/b21e8011-0428-4421-b5d4-6e508cb0d579)

---

### 🖥️ Target Machine Setup

1. **🛠️ Change Hostname**: Set the hostname to `Target-PC`.
2. **🔗 Assign Static IPv4 Address**: Assign a static IP to the target machine.

   ![IPv4 Configuration](https://github.com/NRM10101/Active-Directory-/assets/126091408/419b350b-a15b-4016-8074-7984c21b3688)

3. **⬇️ Download Splunk Universal Forwarder**: 
   - Go to [Splunk.com](https://www.splunk.com), log in, and download the **Splunk Universal Forwarder**.
   - Install it.

   ![Download Splunk](https://github.com/NRM10101/Active-Directory-/assets/126091408/198589e7-ea6a-442c-8a19-886f9ffb8597)

4. **⬇️ Download and Install Sysmon**:
   - Sysmon (System Monitor) is a Windows service and driver that logs detailed system activity to the event log. It tracks process creations, network connections, and changes to file creation times, helping to detect and investigate malicious activity. It's part of the Sysinternals suite and is used for advanced monitoring and forensic analysis.
   - Download **Sysmon** from the Sysinternals suite.
   - Use [sysmon-modular](https://github.com/olafhartong/sysmon-modular) for configuration.
   - Download the `sysmonconfig.xml`.
   - Install Sysmon with the downloaded configuration file.

   ```bash
   sysmon -accepteula -i sysmonconfig.xml
   ```

   ![Sysmon Setup](https://github.com/NRM10101/Active-Directory-/assets/126091408/6587b4fb-a91f-4a8d-b3fd-293f2659c550)

5. **⚙️ Configure Splunk Forwarder**:
   - Now we need to instruct our splunk forwarder on what we want to send over to our Splunk Server.To do this we must configure a file called inputs.conf. For this we use inputs.conf file from github
   - Modify the `inputs.conf` file.

   ![inputs.conf Configuration](https://github.com/NRM10101/Active-Directory-/assets/126091408/31c395a3-e13f-46ac-80db-944dcc47caa8)

   - Change Splunk Forwarder logon as **Local System**. as follows.
     
   ![Splunk Forwarder Logon](https://github.com/NRM10101/Active-Directory-/assets/126091408/00203270-885a-4042-af59-f3a403c91cf0)

   - Restart the service.
   - Now we have Sysmon installed and Universal forwarder installed along with updated inputs.conf

7. **🌐 Access Splunk Server**:

   ![image](https://github.com/user-attachments/assets/34ab7b0d-3eac-4a0a-93b1-47e87f650e50)

   - Log in to the Splunk server.

   ![image](https://github.com/user-attachments/assets/a670d171-b116-487a-a002-4e932af33893)

   - Create an index named **endpoint**.
   - Ensure that Splunk server is set to receive data.
   - `Forwarding and Receiving`

   ![image](https://github.com/user-attachments/assets/3ba2b928-1e7c-4ff1-bd60-14c13b4aad7d)

   - If we everything setup correctly. Verify that data from the target machine is being received.

   ![Splunk Data Received](https://github.com/NRM10101/Active-Directory-/assets/126091408/d9fb2454-36ec-4058-a158-6089bc1273f6)

---

### 🛠️ Active Directory (Windows Server) Setup

1. **🛠️ Change Hostname**: Set the hostname to `ActiveDirectory`.
2. **🔗 Assign Static IPv4 Address**: Assign IP `192.168.10.7`.
3. **⬇️ Download Splunk Universal Forwarder**: Install it on the Windows server.
4. **⬇️ Download and Install Sysmon**: Follow the same process as for the target machine.
   - Download Sysmon.
   - Use the [sysmon-modular](https://github.com/olafhartong/sysmon-modular) configuration.
   - Install Sysmon with the configuration file.

5. **⚙️ Configure Splunk Forwarder**:
   - Now we need to instruct our splunk forwarder on what we want to send over to our Splunk Server To do this we must configure a file called inputs.conf For this we use inputs.conf file from github
   - Modify the `inputs.conf` file.
   
   ![Active Directory Splunk Setup](https://github.com/NRM10101/Active-Directory-/assets/126091408/e752d5ea-9adc-4e0e-90ce-38925954e437)

   - Anytime you update inputs.conf file you must restart splunk universal folder service.
   - Restart the Splunk Forwarder service after updating the configuration.
---

### ✔️ Final Steps

Now that both the **Target Machine** and **Active Directory** have the **Splunk Universal Forwarder** and **Sysmon** configured, verify that the data from both machines is being received by the Splunk server.

Ensure that:
- Both machines are sending data.
- The Splunk server is configured to receive and index the data correctly.

---
