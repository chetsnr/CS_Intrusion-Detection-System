# CS_Intrusion-Detection-System
Snort IDS Setup Guide
This README outlines the steps to set up an Intrusion Detection System (IDS) using Snort on an Ubuntu machine, with a Kali Linux machine for testing.

Prerequisites
Ubuntu machine (for Snort installation)
Kali Linux machine (for testing attacks)
Installation and Configuration Steps
Install Snort on Ubuntu: Open your terminal and run the following command:


sudo apt-get install snort

Check the FTP Configuration: Open the ftp.conf file using gedit:
sudo gedit /etc/snort/ftp.conf

Write Snort Rules: Edit the snort.conf file to include your rules:
sudo gedit /etc/snort/snort.conf

Check IP Addresses: Find the IP addresses of both the Ubuntu and Kali Linux machines. 
You can do this by running:ifconfig

Run Snort as IDS: Use the following command to start Snort in IDS mode:
sudo snort -A console -q -u snort -c /etc/snort/snort.conf -i enp0s3

Here’s what the command options mean:

-A console: Output alerts to the console.

-q: Run in quiet mode (suppress non-error messages).

-u snort: Run Snort as the user "snort".

-c /etc/snort/snort.conf: Specify the configuration file to use.

-i enp0s3: Specify the network interface to monitor (replace enp0s3 with your interface if different).

Test the IDS: On your Kali Linux machine, you can use tools like nmap and ping to simulate an attack:

To scan the Ubuntu machine:
nmap <192.168.1.14>

To ping the Ubuntu machine:
ping <192.168.1.14>

Check for Alerts: After initiating the scans, check the Ubuntu terminal where Snort is running.
You should see alerts indicating any detected threats or searches for your IP address.

Conclusion
You have successfully set up Snort as an IDS on your Ubuntu machine. You can further customize your Snort rules and configurations to enhance detection capabilities.
