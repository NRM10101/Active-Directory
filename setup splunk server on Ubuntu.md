### 🐧 Setting Up Splunk Server on Ubuntu

This section outlines the steps to install and configure the **Splunk Server** on an **Ubuntu** system.

#### 1. **System Requirements**

Before you begin, ensure your Ubuntu server meets the following requirements:

- **Operating System**: Ubuntu 18.04 LTS or later.
- **RAM**: Minimum 8 GB (16 GB or more recommended for larger deployments).
- **Disk Space**: At least 20 GB of free disk space for installation and logs.

#### 2. **Download Splunk Enterprise**

1. Open a terminal and download the latest version of **Splunk Enterprise**:

   ```bash
   wget -O splunk-<version>-<build>.deb 'https://www.splunk.com/page/download_track?file=7.3.4/linux/splunk-<version>-<build>.deb&ac=default&wd=1&ed=un&pl=linux'
   ```

   (Replace `<version>` and `<build>` with the actual version you wish to install.)

#### 3. **Install Splunk Enterprise**

2. Install the downloaded package using `dpkg`:

   ```bash
   sudo dpkg -i splunk-<version>-<build>.deb
   ```

3. Once the installation is complete, enable Splunk to start on boot:

   ```bash
   sudo /opt/splunk/bin/splunk enable boot-start
   ```

#### 4. **Start Splunk**

4. Start Splunk for the first time:

   ```bash
   sudo /opt/splunk/bin/splunk start --accept-license
   ```

5. Set up the admin username and password when prompted.

#### 5. **Configure Splunk Web**

6. By default, Splunk Web runs on port **8000**. Open your web browser and navigate to:

   ```
   http://<your-server-ip>:8000
   ```

   Log in with the credentials you set during the setup.

#### 6. **Enable Receiving Data**

7. To allow data forwarding from other machines, configure Splunk to listen for incoming data:

   - Go to **Settings** > **Data** > **Data Inputs**.
   - Click on **Forwarded Data** and enable the desired input methods (e.g., TCP).

#### 7. **Firewall Configuration (if necessary)**

8. If your server has a firewall, ensure that port **8000** (for Splunk Web) and the designated receiving ports are open:

   ```bash
   sudo ufw allow 8000
   sudo ufw allow <your-receiving-port>
   ```

#### 8. **Verify Installation**

9. After completing the installation, verify that Splunk is running:

   ```bash
   sudo /opt/splunk/bin/splunk status
   ```

   ![image](https://github.com/user-attachments/assets/67b2ba21-0ea0-49c6-ac02-f4c307ee145f)


