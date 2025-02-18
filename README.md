
# pfSense Firewall Installation and Configuration

## Introduction
This project documents the installation and configuration of pfSense, an open-source firewall solution. The setup is performed in a virtualized environment using VirtualBox, focusing on configuring network interfaces, setting up basic firewall rules, and ensuring network segmentation.

## Environment Setup
### Downloading and Preparing pfSense
1. Download the pfSense ISO file from the official website.
2. Create an account to access and download the Netgate installer.
3. Extract the ISO image for use in VirtualBox.

### Creating a Virtual Machine in VirtualBox
1. Open VirtualBox and create a new virtual machine.
2. Allocate 2GB of RAM, one CPU core, and 25GB of disk storage.
3. Assign two network adapters:
   - **WAN Adapter**: Set as a **bridged adapter** for internet connectivity.
   - **LAN Adapter**: Set as a **NAT adapter** for internal network communication.
4. Attach the pfSense ISO image and boot the virtual machine.

## pfSense Installation
1. Follow the installation prompts to configure Netgate.
2. Select the appropriate **WAN interface** using the IPv6 address.
3. Select the **LAN interface** and proceed with default settings.
4. Complete the installation and reboot the virtual machine, ensuring the ISO file is removed.

## Accessing the pfSense Web Interface
1. Ensure the Windows 10 virtual machine is on the same network as pfSense.
2. Open a web browser and enter the pfSense machine’s IP address.
3. Log in using the provided credentials.
4. Complete the setup wizard, keeping most default settings.
5. **Disable the "Block RFC 1918 Networks" option** to allow WAN connectivity in this environment.

## Configuring Firewall Rules
### Understanding Rule Processing
- Firewall rules in pfSense are **read from top to bottom**.
- Rules should be structured carefully to allow or deny traffic as required.

### Creating Basic Rules
1. **Block All Traffic**: A default rule at the top to deny all incoming traffic.
2. **Allow Specific Traffic**:
   - Add virtual machines to the network and configure their permissions.
   - Allow traffic from a Kali Linux virtual machine.
   - To test rule effectiveness, block ICMP (ping) traffic from Kali to Windows 10.
   - Allow ICMP traffic again to confirm rule application.
   - Allow TCP traffic from Kali Linux.
3. Ensure these rules are placed **below the implicit deny rule** to enforce network segmentation properly.

## Conclusion
This project demonstrated the installation and configuration of pfSense in a virtualized environment, including firewall rule creation and network segmentation. Future enhancements may include additional security hardening, advanced rule configurations, and third-party package installations for extended functionality.
