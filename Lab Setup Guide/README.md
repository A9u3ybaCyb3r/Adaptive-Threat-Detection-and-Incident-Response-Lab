# Lab Setup

## Table of Contents
1. [Planning Phase](#planning-phase)
2. [Create a new NAT Network](#create-a-new-nat-network)
3. [Setting up Ubuntu Desktop](#setting-up-ubuntu-desktop)
4. [Installing Splunk on Ubuntu](#installing-splunk-on-ubuntu)
5. [Installing Snort](#installing-snort)
6. [Setting up Kali Linux](#setting-up-kali-linux)
7. [Building an Active Directory](#building-an-active-directory)
8. [Installing Splunk Forwarder](#installing-splunk-forwarder)
9. [Installing LimaCharlie](#installing-limacharlie)
	- [Deploying Endpoint Agents](#deploying-endpoint-agents) 
10. [Installing Sysmon](#installing-sysmon)

---

## Planning Phase

First, we build the network architecture for the lab environment using [Draw.io](https://www.drawio.com/). This includes creating a detailed network diagram outlining the Active Directory Security Lab's structure, components, and connections. The diagram helps visualize how different elements interact, ensuring a well-organized setup for testing and security exercises.

- [Network Diagram](https://github.com/A9u3ybaCyb3r/Adaptive-Threat-Detection-and-Incident-Response-Lab/blob/main/Lab%20Setup%20Guide/ATDIR%20Lab%20Network%20Diagram.drawio.pdf)


## Creating a New NAT Network in VirtualBox

1. Open VirtualBox and go to **File > Tools > Network Manager**.

   ![image](https://github.com/user-attachments/assets/ec55021a-a04e-43d4-9d00-97e9e2fb3717)

2. In the **Network Manager**, select the **NAT Network** tab and click **Create** to create a new network.

   ![image](https://github.com/user-attachments/assets/440ede8a-f2be-4438-9d5c-3e2f7cfc3101)

3. Configure the network by setting your preferred **name** and **IP address range**.

   ![image](https://github.com/user-attachments/assets/8565b6fa-bb0b-498b-8d4c-ee3aded21032)

---

## Setting up Ubuntu Desktop

### Download the ISO File

[Download Ubuntu Desktop ISO](https://ubuntu.com/download/desktop)

### Create the Ubuntu Machine

1. Create a virtual machine.

   ![image](https://github.com/user-attachments/assets/c1fb78f6-e41d-4b8a-aa85-61003cec5ece)

2. Increase the RAM.

   ![image](https://github.com/user-attachments/assets/3e96eb97-22e1-4768-b1f6-fc5cfccd9123)

3. Increase the storage.

   ![image](https://github.com/user-attachments/assets/8cc68869-cbdf-46cb-a230-f04a27029d6d)

4. Set your network to **NAT Network**, and choose the name of the network that you created, then click **OK**.

   ![image](https://github.com/user-attachments/assets/1c22e291-17bb-4247-985f-dc98c2fdad6e)

### Installing Ubuntu Desktop

1. Hit **Start** to turn on the machine.

   ![image](https://github.com/user-attachments/assets/69a5dbdf-5af8-4cba-ae86-e9661c273662)

2. Hit **ENTER** on **Try or Install Ubuntu**.

   ![image](https://github.com/user-attachments/assets/f0762659-8f0e-4380-bfad-4236a95fd5d1)

3. Choose your **Language**.

   ![image](https://github.com/user-attachments/assets/3d4084f9-e655-49f1-b5bc-88bba873c63b)

4. Hit **Next**.

   ![image](https://github.com/user-attachments/assets/0b8d9dda-803a-42d5-9531-5ea8e2fb0daa)

5. Choose your **Keyboard Language**.

   ![image](https://github.com/user-attachments/assets/59893904-4886-4970-b923-acd221d8890e)

6. Hit **Next**.

   ![image](https://github.com/user-attachments/assets/caea4edb-8adf-4cf0-8697-d8f9512bb152)

7. Install Ubuntu and hit **Next**.

   ![image](https://github.com/user-attachments/assets/7d4266ef-95f3-44ca-8472-b6d3b428af81)

8. Hit **Next**.

   ![image](https://github.com/user-attachments/assets/9e9c120b-7281-4462-bb23-91e506f42a28)

9. Hit **Next**.

   ![image](https://github.com/user-attachments/assets/b2e84545-b8e0-4563-a535-957a6c96c79c)

10. Hit **Next**.

    ![image](https://github.com/user-attachments/assets/f99918f9-f678-4618-874f-59644379867e)

11. Hit **Next**.

    ![image](https://github.com/user-attachments/assets/fa2b1daa-5c6b-4678-b779-b58ea683562a)

12. Create your account.

    ![image](https://github.com/user-attachments/assets/dbb70d73-3c75-44a6-b3e4-03c6a8ed068c)

13. Choose your time zone.

    ![image](https://github.com/user-attachments/assets/7164ebbb-1967-46ce-8016-0b580ddba58d)

14. Hit **Install** and wait for the installation to complete.

    ![image](https://github.com/user-attachments/assets/0387d603-cf67-4d5f-b093-c8c7c23fe0ad)

15. Hit **Restart** and log in to the machine with your profile.

    ![image](https://github.com/user-attachments/assets/b7d28532-c722-4c24-9c90-ed6efcfde3b1)

16. Update system packages using the command: 

    ```bash
    sudo apt update
    ```

    ![image](https://github.com/user-attachments/assets/b3777a70-67a7-4879-89ee-5448b82363dc)

17. Install required packages using the command:

    ```bash
    sudo apt install bzip2 tar gcc make perl git
    ```

    ![image](https://github.com/user-attachments/assets/f0fd8c7d-550a-4b56-b014-7a4386c0818c)

18. Install the generic kernel headers using the command:

    ```bash
    sudo apt install linux-headers-generic
    ```

    ![image](https://github.com/user-attachments/assets/2e92508d-8e3d-4ef7-9fd5-b59693e8c0e6)

19. Install the system-specific kernel headers using the command:

    ```bash
    sudo apt install linux-headers-$(uname -r)
    ```

    ![image](https://github.com/user-attachments/assets/2b93e0dd-f7f9-4f0d-b6b2-804ad9003573)

20. Install Guest Additions on the machine.

    ![image](https://github.com/user-attachments/assets/5ef60e06-c2e3-4a0b-a5d2-88db608a929c)

21. Open a terminal on the disk that was just added.

    ![image](https://github.com/user-attachments/assets/967d8a4b-7973-4216-bd24-9a3072fb3311)

22. Run the VirtualBox additions.

    ![image](https://github.com/user-attachments/assets/7a3d48c2-1009-4457-bf5b-aaad289761d6)

### Setting an IP Address to the Machine

1. Open a terminal and run the command: 

    ```bash
    ip a

You can view the current IP of the machine.

![image](https://github.com/user-attachments/assets/9a659493-91b2-40b3-8e72-201f6522a7af)

2. Go to the network settings of the machine.

   ![image](https://github.com/user-attachments/assets/2d9b0143-1c74-4a98-9465-5e42a2791d5b)

3. Click on the settings.

   ![image](https://github.com/user-attachments/assets/95176f40-0f24-480e-946a-b61ba95e36d6)

4. Go to **IPv4** and configure the IP, subnet, and gateway. Then hit **Apply**.

   ![image](https://github.com/user-attachments/assets/1c3aa72a-e5ad-4703-bbe8-12dbbf82a2ba)

5. Confirm the IP address using the command:

   ```bash
   ip a

![image](https://github.com/user-attachments/assets/b56054d4-b4ae-430e-8cf0-5d13052231f4)

---

## Installing Splunk on Ubuntu

### Download Splunk Enterprise

1. Go to [Splunk's download page](https://www.splunk.com/en_us/download.html).
2. Log in and download the Splunk Enterprise version.

   ![image](https://github.com/user-attachments/assets/3bfd482a-7018-4085-8285-9fddaa2efa7f)

3. Grab the Linux `.tgz` version of Splunk.

   ![image](https://github.com/user-attachments/assets/213e9d53-a073-46fa-a903-2673b09b2b03)

### Install Splunk on Ubuntu

1. Open a terminal and navigate to the Downloads folder. Run the following command to extract the Splunk archive:

   ```bash
   sudo tar xvzf splunk-file.tgz -C /opt

![image](https://github.com/user-attachments/assets/1647559c-cd30-4931-a285-bd8185e2b0ca)

2. Change to the Splunk directory:

   ```bash
   cd /opt/splunk/bin

![image](https://github.com/user-attachments/assets/5267939f-0a7b-4e22-a306-8b1d6978ad63)

![image](https://github.com/user-attachments/assets/0dd806ab-e1bd-4de4-bb6c-3e98f04d04d4)

3. Start Splunk and accept the license:

   ```bash
   sudo ./splunk start --accept-license

![image](https://github.com/user-attachments/assets/ecbe0a05-e233-4292-9725-a63e8a3dc700)

4. You will be prompted to create a username and password for Splunk.

![image](https://github.com/user-attachments/assets/3b6cec53-95f2-4b7b-b963-87c7d916b1a3)

### Access the Splunk Web Interface

1. Open a web browser and navigate to one of the following URLs to access the Splunk web interface:

- `http://localhost:8000`
- `http://<your-ubuntu-ip>:8000` (if accessing from another machine)

![image](https://github.com/user-attachments/assets/9a7ac6a4-87eb-44d3-826e-69d271bda6bd)

2. To access the web interface from another machine, use the IP address of your Ubuntu server.

![image](https://github.com/user-attachments/assets/b7600173-eff5-4b40-bbf9-588d53e2a6b9)

3. Log in using the credentials you created during installation.

![image](https://github.com/user-attachments/assets/37b467ee-f995-458c-bbb4-b520bd39fe61)

![image](https://github.com/user-attachments/assets/c376e027-79b0-4898-9cca-f6362db9f9f4)

4. After logging in, you should see the Splunk dashboard.

![image](https://github.com/user-attachments/assets/9ca05a5d-2008-4f18-8289-9f4516b20888)

5. To have Splunk start automatically when the machine boots, run:

   ```bash
   sudo ./splunk enable boot-start

![image](https://github.com/user-attachments/assets/2e1ced1f-1e41-4a01-8d79-dc6b6865dec6)

### Managing Splunk on Your Lab Machine

1. To stop the Splunk service, use:

   ```bash
   sudo /opt/splunk/bin/splunk stop

2. To disable Splunk from starting automatically at boot:

   ```bash
   sudo systemctl disable splunk

3. If needed, you can re-enable it later with:

   ```bash
   sudo systemctl enable splunk

---

## Installing Snort

1. Open a terminal and run:

	```bash
	sudo apt install snort

- Enter your password if prompted.

- During installation, Snort will ask for the local network address range. You can find this information using:

	```bash
	ifconfig

- Note your IP address and subnet mask. For example, if your IP is `192.168.1.4` and subnet mask is `255.255.255.0`, the network range is `192.168.1.0/24`.

2. Verify the installed version:

	```bash
	snort --version

3. Directory and Files Overview

- Configuration File: Located at `/etc/snort/snort.conf`. This file controls Snort's settings, including network variables and rules.

- Rules Directory: `/etc/snort/rules/` contains predefined rule files for detecting malicious activity.

4. Before making changes:

	```bash
	sudo cp /etc/snort/snort.conf /etc/snort/snort.conf.bak

### Editing Configuration

1. Open the configuration file:

	```bash
	sudo nano /etc/snort/snort.conf

2. Set Network Variables:

- `HOME_NET`: Defines the monitored subnet. For example:

	```bash
	var HOME_NET 192.168.1.0/24

- `EXTERNAL_NET`: Defines the external network. Use:

	```bash
	var EXTERNAL_NET any

- Rule Configuration: Locate the rules section and ensure it points to your rule files:

	```bash
	include $RULE_PATH/local.rules
	include $RULE_PATH/backdoor.rules

### Testing Configuration:

1. Validate configuration changes using:

	```bash
	sudo snort -T -c /etc/snort/snort.conf

- A successful test ensures that changes don't introduce errors.

2. Practical Usage:

- Sniffer Mode:

	```bash
	sudo snort -i <interface>

3. Displays captured packet headers.

- Packet Logger Mode: Stores packets in files for analysis.

- IDS/IPS Mode: Implements rule-based monitoring and prevention.

---

## Setting up Kali Linux

### Downloading Kali Linux Virtual Machine Image

1. Go to [Kali's official download page](https://kali.org/get-kali/).
2. Click on **Virtual Machines** and download the 64-bit version for VirtualBox.

   ![image](https://github.com/user-attachments/assets/ae2d558e-57a4-4d1a-8576-5ad25de659ec)
   
   ![image](https://github.com/user-attachments/assets/6430026d-9ca1-46db-9dd6-98e6d758617c)

### Importing Kali Linux into VirtualBox

1. After downloading, extract the `.ova` file.
2. Open VirtualBox, click **Add**, and select the `.vbox` extension file from the extracted contents.

   ![image](https://github.com/user-attachments/assets/37ef160d-c250-4151-80df-bdfb038f063c)
   
   ![image](https://github.com/user-attachments/assets/5cf67d2e-ebd6-4c6e-ab83-f49f87a27b82)

### Configuring Network Settings

1. Right-click on the Kali Linux machine in VirtualBox, then select **Settings > Network**.

   ![image](https://github.com/user-attachments/assets/465b1135-d2b9-4e79-aa75-f6eb9f315ed1)

2. Change the network adapter to the **NAT Network** that you created.

   ![image](https://github.com/user-attachments/assets/13a03bdb-84e5-4cad-bac3-aa89af5adb77)

### Adjusting System Resources

1. To allocate more RAM, go to **Settings > System > Motherboard**. Increase the RAM based on your system’s resources (e.g., 8GB for resource-intensive tools).

   ![image](https://github.com/user-attachments/assets/9cf482b6-64c7-48be-8248-fe25ad5868eb)

### Starting Kali Linux

1. Click **OK** to save the settings, then start the machine.
2. Login using the default credentials: `kali` for both the username and password.

   ![image](https://github.com/user-attachments/assets/919a0fe4-12fe-4847-acad-0180f51a77b8)

---

## Building an Active Directory

## Setting Up Windows Server and Domain Controller

### Downloading the ISOs

### Step 1: Visit Microsoft Evaluation Center
1. Go to Google and search for "Microsoft Evaluation Center."
   - Official link: [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter)
2. Open the official Microsoft Evaluation Center page from the search results.

### Step 2: Browse Available Software
- The Evaluation Center offers trial versions of Windows, Windows Server, SQL Server, and more.
- For this lab, download **Windows 10 Enterprise** and **Windows Server 2022**.

### Step 3: Download Windows 10 Enterprise
1. Select **Windows 10 Enterprise** from the list.
2. Choose the **64-bit ISO** version for your region (e.g., United States).
3. Fill out the registration form (generic information is acceptable).
4. Click **Download Now** to start the download.

### Step 4: Download Windows Server 2022
1. Select **Windows Server 2022** and open the download page.
2. Choose the **64-bit ISO** version.
3. Complete the registration form, then click **Download Now** to begin.

### Step 5: Notes
- Note that these downloads are large (Windows 10 Enterprise is ~5.2 GB, Windows Server 2022 is ~4.7 GB).
- After 90 days, the OS may prompt for activation or start shutting down if inactive. Reboot as needed for testing.

---

## Setting Up the Domain Controller

### Step 1: Create a New Virtual Machine
1. In VirtualBox, select **Create a New Virtual Machine**.
2. Choose the **Typical** setup option.
3. Name it `Jarvis-DC`
4. Browse for the **Windows Server 2022 ISO** file you downloaded and select it.

### Step 2: Operating System Selection
- Choose **Windows Server 2016** if Windows Server 2022 isn’t listed. This won’t affect the setup.

### Step 3: Configure Disk Space
- Allocate **at least 60 GB** of disk space.
- Select the option to **Split virtual disk into multiple files** for efficient disk space use.

### Step 4: Adjust Virtual Machine Settings
1. Open **Edit Virtual Machine Settings**.
2. Set memory to **4–8 GB** (8 GB recommended if available).
3. Remove any **floppy disk device** if it appears.
4. Go to **Network** and change the network settings
   - Choose the **NAT Network** that you created.

![image](https://github.com/user-attachments/assets/455954ea-2dac-402d-b682-bbda225868c6)

### Step 5: Power On and Install Windows Server
1. Power on the virtual machine.
2. Press any key to boot from the ISO when prompted.
3. Follow installation prompts, choosing:
   - **Language and region** (defaults are typically fine).
   - **Standard Evaluation Desktop Experience** as the installation type.
   - Accept **license terms**.
   - **Custom installation** on Drive 0 (unallocated space).

### Step 6: Complete Initial Setup
- After installation, Windows will reboot.
- Set an **administrator password** (e.g., `#IronMan`).

### Step 7: Install Virtualbox Tools (Optional but Recommended)
1. In Virtualbox, go to **Devices > Insert Guest Additions CD image**.
2. Run the `amd64` file from the **This PC** to install the tools.
3. Choose the **Complete** installation option, then finish and reboot if needed.

![image](https://github.com/user-attachments/assets/6799f85a-7a14-4948-b6fb-c3ce1a67cf8e)

![image](https://github.com/user-attachments/assets/16995426-5122-4ead-bc4d-5849a19ecf5e)

### Step 8: Rename the Computer
1. Open the Start menu and search for **View your PC name**.
2. Click **Rename this PC**.
3. Name your domain controller (e.g., **Jarvis-DC**).
4. Restart the virtual machine after renaming.

### Step 9: Reboot and Continue
- Allow the machine to restart.
- Once logged back in, continue with additional domain controller configurations as needed.

---

## Making the Machine a Domain Controller

### Step 1: Open Server Manager
- Open Server Manager, then select **Manage > Add Roles and Features**.

### Step 2: Roles and Features Wizard
1. Click **Next** on the introduction screen.
2. Choose **Role-based or feature-based installation** and click **Next**.
3. Select the server (e.g., "Jarvis-DC") and click **Next**.

### Step 3: Select AD DS
1. Select **Active Directory Domain Services** and add any required features when prompted.
2. Click **Next** until you reach the **Install** button, then start the installation.
3. Wait for the installation to complete.

### Step 4: Promote to Domain Controller
1. After installation, click **Promote this server to a domain controller**.
2. Choose **Add a new forest** and enter a root domain name (e.g., `StarkTech.local`).
3. Click **Next** and set the Forest and Domain functional levels (e.g., 2016).
4. Set the **Directory Services Restore Mode (DSRM) password**.
5. Use the Password that you use for **Administrator** of the server. Then hit **Next**.

### Step 5: Configure NetBIOS and Paths
1. Accept the automatically generated NetBIOS domain name.
2. Proceed with default paths for **NTDS, SYSVOL**, etc.
3. Click **Install** and let the server reboot after installation.

### Step 6: Log into the Domain
- After reboot, log in using the new domain (e.g., `StarkTech\Administrator`) and the Administrator password.
  
---

## Setting Up Active Directory Certificate Services (AD CS)

### Step 1: Add Roles and Features for AD CS
1. In Server Manager, select **Manage > Add Roles and Features**.
2. Choose **Role-based or feature-based installation** and proceed by clicking **Next**.
3. Select **Active Directory Certificate Services** and add required features.

### Step 2: Install Certificate Authority
1. Continue through the wizard and select **Certification Authority**.
2. Enable **Restart if required**, then click **Install**.



### Step 3: Configure AD CS
1. After installation, select **Configure Active Directory Certificate Services**.
2. Choose **Certification Authority** and set it up as an **Enterprise CA** and **Root CA**.
3. Create a **New Private Key** and use default cryptographic settings (e.g., SHA-256).
4. Set the **Validity Period** to 99 years for long-term lab setup.
5. Click **Next**, review settings, then **Configure**.

### Step 4: Reboot
- After configuration, restart the server to finalize setup.

## Setting Up User Virtual Machines for Lab

## Step 1: Shut Down the Domain Controller
- Shut down the domain controller to free up resources, especially if working with limited RAM or storage.

## Step 2: Create New Virtual Machines
1. Open **Virtualbox** and select **Create a New Virtual Machine**.
2. Select the **ISO file for Windows 10** (instead of the Windows Server ISO used for the domain controller).
3. Click **Next** to proceed through setup steps.
4. When prompted, skip entering the **Windows product key**.
5. Select **Windows 10 Enterprise** as the version.

## Step 3: Name the Machines
- Assign unique names to each VM. Examples:
  - **Pepper** (e.g., for one user)
  - **Happy** (for another user)

## Step 4: Configure Virtual Machine Hardware
1. Allocate **60 GB** of disk space and select **Split virtual disk**.
2. Customize hardware settings:
   - Remove the **floppy disk drive**.
   - Set **memory allocation** based on system resources:
     - Use **8 GB** if available, or adjust to **4 GB** or **2 GB** if limited.
   - Use the **Nat Network** that you created for the network adapter, similar to the server.

![image](https://github.com/user-attachments/assets/b808c2d9-7f65-4daa-b74b-2b109534b734)

## Step 5: Power On and Start Installation
1. Power on each VM, and when prompted, press a key to start the boot sequence.
2. Go through the Windows setup:
   - Set language to **English** (or your region’s language).
   - Choose **Custom Install**.
   - Partition the drive by clicking **New** and applying settings, then proceed with **Next** to start the installation.

## Step 6: Complete Windows Installation Steps
1. After installation, reboot each machine as prompted.
2. Select region (e.g., **U.S.**) and keyboard layout.
3. Choose to **skip the second keyboard layout**.

## Step 7: Configure User Accounts
1. When prompted to sign in with Microsoft, select **Domain Join Instead**.
   - For Pepper:
     - **Username**: Pepper Potts
     - **Password**: Password1
   - For Happy:
     - **Username**: Happy Hogman
     - **Password**: Password2
2. Set security questions with generic answers (e.g., answer each with "Bob").

## Step 8: Disable Optional Settings
- Skip optional settings like **advertising**, **location services**, and **Cortana setup**.

## Step 9: Install Virtualbox Tools
1. In each **Devices**, install **Virtualbox Tools** to enable full-screen mode and improved performance.
2. Perform a **Complete Install** and restart if prompted.
3. Adjust display settings if needed.

## Step 10: Rename Each VM for Identification
1. Rename **Pepper Potts** machine as **Pepper**.
2. Rename **Happy Hogman** machine as **Happy**.

## Step 11: Final Reboot
- Restart each machine after renaming to complete the setup process for both VMs.

Once these steps are complete, both user machines should be ready. The next step is to join them to the domain when you power on the domain controller again.

## Setting Up Users, Groups, Policies, and Configurations on a Windows Server Domain Controller

## Step 1: Boot up the Domain Controller
1. Power down any non-essential virtual machines (e.g., workstations named Pepper Potts and Happy Hogman).
2. Start the Domain Controller (Windows Server 2022, named as Windows Server 2016 in this example) and log in.

## Step 2: Access Active Directory Users and Computers
1. Open **Server Manager** on the domain controller.
2. Navigate to **Tools > Active Directory Users and Computers**.
3. Observe the existing **Organizational Units (OUs)**, users, and groups.

## Step 3: Create Organizational Units (OUs) for Users and Groups
1. Right-click on the root of your domain (e.g., Empire.local), select **New > Organizational Unit**, and name it **Groups**.
2. Move default system groups (e.g., Domain Admins, Enterprise Admins) into the **Groups OU** for organizational clarity.

## Step 4: Create New User Accounts
1. **Tony Stark (Domain Admin)**:
   - Right-click the existing **Administrator** account, select **Copy**, and create a new user with the following:
     - Full Name: **Tony Stark**
     - Username: **tstark**
     - Password: **Password12345!**
     - **Password Never Expires**: Enabled
2. **SQL Service Account (for demonstration)**:
   - Copy the **Administrator** account and create a new service account with the following:
     - Full Name: **SQL Service**
     - Username: **SQLService**
     - Password: **MyPassword123!**
     - Add a description for demonstration purposes: "Password is MyPassword123!".
3. **Standard Users (Pepper Potts and Happy Hogman)**:
   - Create individual user accounts as follows, **Right-click black space > New > User **:
     - **Pepper Potts**:
       - Username: **ppotts**
       - Password: **Password1**
       - **Password Never Expires**: Enabled
     - **Happy Hogman**:
       - Username: **hhogman**
       - Password: **Password2**
       - **Password Never Expires**: Enabled

## Step 5: Configure an SMB File Share
1. In **Server Manager**, go to **File and Storage Services > Shares**.
2. Click **Tasks > New Share**, and select **SMB Share - Quick**.
3. Choose a share location on the **C:** drive, name the share **JarvisShare**.
4. Complete the configuration with default settings and hit **Create**.
5. The network path should look like `\\Jarvis-DC\JarvisShare`.

## Step 6: Set up a Service Principal Name (SPN) for the SQL Service Account
1. Open **Command Prompt** as Administrator.
2. Use the following command to set up an SPN for the SQL service account:
   ```shell
   setspn -a Jarvis-DC/SQLService.StarkTech.local:60111 StarkTech\SQLService
3. Verify the SPN by querying with:
   ```shell
   setspn -T StarkTech.local -Q */*
4. If you see the message **Existing SPN found!** you are done.

## Step 7: Create a Group Policy to Disable Microsoft Defender (Optional)
`In my case I will not do it in order to keep as real as possible the assessment`
1. In Server Manager, **Tools** open Group Policy Management.
2. Expand **Forest: StarkTech.local > Domains > Empire.local.**
3. Right-click StarkTech.local and select **Create a GPO** in this domain. Name it Disable Windows Defender.
4. Right-click the new GPO and select **Edit**. Navigate to:
    ```shell
    Computer Configuration > Policies > Administrative Templates > Windows Components > Microsoft Defender Antivirus
5. Double-click **Turn off Microsoft Defender Antivirus**, set it to **Enabled**, then click **Apply** and **OK**.
6. Enforce the policy by right-clicking the GPO and selecting Enforce.

## Step 8: Set a Static IP Address
1. Go to **Network & Internet Settings > Change adapter options**.
2. Open **Properties** for the network adapter, and configure IPv4 settings:
   - **IP Address**: 10.19.19.250 (Static IP of the Domain Controller)
   - **Subnet Mask**: 255.255.255.0
   - **Default Gateway**: 10.19.19.2 (NAT Network that you created)
   - **Preferred DNS server**: 10.19.19.250

![image](https://github.com/user-attachments/assets/452ae5c4-3877-44af-9067-923a91fb651c)

3. Apply the settings.


## Final Notes
- Confirm all configurations are as expected.
- Ensure the domain controller is correctly configured for user authentication, file sharing, and group policies before running further security tests.

## Joining Machines to the Domain (StarkTech.local)

This guide outlines the steps to join client machines to the StarkTech.local domain, configure network settings, set up user roles, and verify shared drive access.

## Step 1: Adjust RAM Allocation (If Necessary)

- **Windows Server**: 2 GB (unless more RAM is available).
- **Pepper Machine**: 4 GB.
- **Happy Machine**: 2 GB (optional, you can allocate 4 GB for better performance).

## Step 2: Power On All Machines

- Start the domain controller (DC) and both client machines (Pepper and Happy).
- Log in with the default local admin password (`Password1` for Pepper and `Password2` for Happy).

## Step 3: Configure Network Settings on Each Machine

1. Open **Network and Sharing Center**:
   - Go to **Change Adapter Settings**.
   - Right-click on **Ethernet0** and choose **Properties**.
   - Select **Internet Protocol Version 4 (TCP/IPv4)**, then **Properties**.

2. **Set Static IP and DNS**:
   - Use the domain controller’s IP as the DNS server (e.g., `10.19.19.250`).
   - Save the settings.

## Step 4: Join Each Machine to the Domain (Empire.local)

1. On each machine:
   - Go to **Settings > Accounts > Access work or school**.
   - Select **Connect** and choose **Join this device to a local Active Directory domain**.

2. **Enter the Domain Information**:
   - **Domain Name**: `StarkTech.local`
   - **Username**: `Administrator`
   - **Password**: (use the administrator password for the DC).

3. For the **Account Type** choose `Administrator`
4.  **Restart Each Machine** once they’re successfully joined.

## Step 5: Verify Domain Join on Domain Controller

- On the DC, open **Active Directory Users and Computers**:
   - Navigate to **Computers** in the **StarkTech.local** domain.
   - Ensure **Potts** and **Happy** appear in the list.

## Step 6: Configure Local Users and Groups on Each Client Machine

1. **Enable and Set Password for the Local Administrator Account**:
   - Go to **Computer Management > Local Users and Groups > Users**.
   - Double-click on **Administrator**, set the password (`Password1!`), and enable the account.

2. **Add Domain Users as Local Administrators**:
   - Go to **Computer Management > Local Users and Groups > Groups > Administrators**.
   - Add `ppotts` as a local administrator on **Pepper-Computer**
   - Add `hhogman` as local administrators on **Happy-Computer**.

## Step 7: Enable Network Discovery

- On each client, go to **Network & Sharing Center > Change advanced sharing settings**:
   - Turn on **Network discovery** and **File and printer sharing**.

## Step 8: Map the Shared Drive (JarvisShare) on Happy

1. Open **File Explorer**:
   - Go to **This PC > Map Network Drive**.

2. **Set Drive Mapping**:
   - Choose a drive letter (e.g., `Z:`).
   - Enter the path `\\Jarvis-DC\JarvisShare`.
   - Select **Connect using different credentials**.
   - Use the **Administrator** account and password for authentication.
   - Check the box for **Remember my Credentials**

## Step 8: Verify Access to Shared Drive

- Ensure the **JarvisShare** shared drive is accessible on **Happy**.

## Step 9: Loggin to the machines with the domain users created

- To log in to the machines, use the created domain credentials.
- Computer: **Pepper-Computer**
- Username: `StarkTech\ppotts`
- Password: `Password1`
- Computer: **Happy-Computer**
- Username: `StarkTech\hhogman`
- Password: `Password2`


By following these steps, your machines should now be correctly joined to the **StarkTech.local** domain with all necessary configurations for domain access, shared drive mapping, and user roles.

---

## Installing Splunk Forwarder

### Deployment Steps
1. **Configuring the Splunk Indexer to Receive Data**

	- Navigate to **Settings > Data > Forwarding and Receiving** in Splunk.

	- Under **Configure Receiving Data**, click **Add New** and specify the port for listening (default: 9997).

	- Save the configuration to prepare the indexer for receiving forwarded events.

2. **Installing the Splunk Universal Forwarder**
	- Download the Universal Forwarder from Splunk's official site: https://www.splunk.com/en_us/download/universal-forwarder.html
	- Use a mass deployment tool (e.g., GPO, Ansible) for enterprise environments or manually download the MSI for testing purposes.
	- During installation:
		- Select **Security** and **System Logs** to forward.
		- Specify the Splunk server's IP address and port (default: 8089 for management and 9997 for telemetry).
		- Complete the installation.
4. **Configuring Firewall Rules**
	- Allow Splunk's necessary ports (8089 and 9997) in **Windows Defender Firewall** for both inbound and outbound rules.
	- Create rules under **Advanced Settings**:
		- **Inbound Rule**: Allow TCP ports 8089 and 9997.
		- **Outbound Rule**: Allow TCP ports 8089 and 9997.
		- Name the rules "Splunk Forwarder."
5. **Verifying Data Transmission**
	- In Splunk, go to **Apps > Search & Reporting**.
	- Click **Data Summary** and verify the host and event logs appear.
	- Run a basic query to confirm events are being indexed:

	```spl
	index=* | stats count by host, sourcetype


---

## Installing LimaCharlie

1. Create an Account:

- Visit LimaCharlie.io and sign up using an email or other authentication methods.

- Verify your email to proceed.

2. Set Up an Organization:

- Enter your organization’s name.

- Select a data residency region for storage compliance (e.g., Canada).

- Enable demo configuration for a pre-populated environment or choose a pre-made template (e.g., incident response).

   - In our case we are going to to leave the demo configuration with no pre-configurations

### Deploying Endpoint Agents

1. Define Logical Groupings with Installation Keys

- Navigate to the Installation Keys section in the LimaCharlie dashboard.

- Create installation keys based on endpoint categories. Examples:
   
   - Windows Lab Workstations: For Windows systems used in lab environments.
   
   - Linux Servers: For production or lab Linux servers.
   
   - Critical Infrastructure: For endpoints requiring log forwarding instead of direct agents.

- Use descriptive tags (e.g., ```workstations```, ```windows```, ```servers```) to simplify management and filtering.

2. Prepare Sensor Binaries

- Download the appropriate agent binary from the Sensor Download section. Ensure compatibility with the endpoint’s architecture and OS:
   
   - For Windows, download the ```Windows 64-bit``` executable.
   
   - For other systems (Linux, macOS, etc.), select the corresponding binary.

- Organize binaries for automated deployment to endpoints.

3. Centralized Deployment

- Integrate agent installation into endpoint provisioning pipelines:
   
   - Embed the sensor in baseline installation images for new endpoints.
   
   - Use configuration management tools (e.g., Ansible, SCCM) to push the agent to existing endpoints.

- Ensure administrative privileges on target endpoints for successful agent installation.

4. Agent Installation

- Deploy the agent using the installation key to link it with the corresponding logical group:

  1. Open a terminal or PowerShell as an administrator on the endpoint.

  2. Execute the downloaded agent binary with the -i option followed by the installation key:

      ```cmd
      ./sensor_binary_name.exe -i <installation_key>
			
   - Confirm successful installation by verifying the agent appears under the Sensors List in the LimaCharlie dashboard.

5. Validate Deployment

- Check the Sensors List to ensure endpoints are properly registered.

- Verify telemetry data collection and connectivity.

- Perform a functional test using built-in commands like ```netstat``` via the Console feature to confirm operational status.

6. Post-Deployment Configuration

- Utilize the metadata provided in the dashboard to configure policies and detection rules for each endpoint group.

- Use the Autoruns feature to inspect and address persistence mechanisms on deployed endpoints.

- Leverage the Console for remote command execution and endpoint management.

---

## Installing Sysmon

1. **Download and Extract**:
	- Available from [Microsoft Sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon).
	- Extract to a directory for use.
2. **Choose a Configuration File**:
	- Use pre-configured templates like:
		- **SwiftOnSecurity Sysmon Config** ([GitHub link](https://github.com/SwiftOnSecurity/sysmon-config)).
			- Default high-quality configuration for baseline monitoring.
		- **Olaf Hartong's Modular Config** ([GitHub link](https://github.com/olafhartong/sysmon-modular)).
			- Modular approach for granular monitoring.
	- These files define what Sysmon monitors and logs.
3. **Run the Installer**:
	- Example command in **PowerShell** (run as Administrator):

		```powershell
		.\Sysmon64.exe -i .\sysmonconfig.xml --accept-eula
		
	- This installs Sysmon and applies the configuration.
4. **Verify Installation**:
	- Use net start to confirm Sysmon is running. Open **services.msc** and verify Sysmon’s status.
	- Check **Event Viewer** under: `Applications and Service Logs > Microsoft > Windows > Sysmon`

---

### Now that we are done with the Lab Setup let's go to the [Preparation Phase](https://github.com/A9u3ybaCyb3r/Adaptive-Threat-Detection-and-Incident-Response-Lab/tree/main/Preparation%20Phase) to configure alerts and integrate logs to Splunk.



