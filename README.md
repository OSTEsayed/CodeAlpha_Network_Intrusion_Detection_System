# CodeAlpha_Network_Intrusion_Detection_System
# Network Intrusion Detection System using Snort

## Features:
- Real-time network traffic analysis
- Rule-based intrusion detection
- Alert generation for suspicious activities
- Logging and reporting of detected intrusions

## Tools & Services Used in this Guide:
- VirtualBox to run the target server.
- kali_linux OS as the Main host.
- Linux server. (Ubuntu server 20.04.4 LTS)
- Snort IDS. (Intrusion Detection System)
- Nmap for performing port Scanning of the target. (Additionally) 
- slowloris for performing DOS attack to target. (Additionally) 
- ssh service to connect to host remotely. 
- apache2 service to run a web app in ubunutu server.


## Guide:

1. First Install VirtualBox (Follow The official instruction from kali docs )
   - https://www.kali.org/docs/virtualization/install-virtualbox-host/
2. Download Ubunutu Server .iso file from the main source 
   - https://ubuntu.com/download/server
3. Set up the Server throw VirtualBox GUI:
   - run VirtualBox
   - Press NEW icon (or Ctrl+N)
   - fill name and the .iso and fellow the instruction.
   - run the new instance and finish the installation steps.
5. install ssh on the ubuntu server (you can skip this step and do the rest mainly in the server command-line)
   - sudo apt install open-ssh
6. install snort IDS  (Intrusion Detection System)  
   - before the installation run "ifconfig" get the network adapter device typename for example "wlan0, or enp0s3", get the inet IP for your server. (you can also run curl ifconfig.me to get the public ip of your server.)
   - sudo apt install snort
   - fill input with server network adapter device type you want to listen on example "enp0s3".
   - fill input with server network IP address and their musk address example "105.103.104.0/24"

7. back to the main OS (kali) and connect to server with ssh service. (you can skip this step and do the rest mainly in the server command-line)
   - ssh username@server_IP_addres
   - enter Password.
8. Check for the configuration file of snort (this is a must before running the IDS) (the location of the config file is /etc/snort/snort.conf) 
   - sudo snort -T -c /etc/snort/snort.conf -i enp0s3    (you will change enp0s3 according to your ifconfig...)
9. run the snort IDS:
   - sudo snort -A console -q -u snort -g snort -c /etc/snort/snort.conf -i enp0s3
Congrats all is set.
10. perform some attacks to check for the functionality of your IDS:
   - nmap -sV server_IP (performing PORT scan attack for the server.)
   - slowloris server_IP -s number_of_attacker (performing a DOS attack to the (server Denial of service attack))


# for additional learning you should :


1. **Configuration:**
   - Set up Snort configuration files for rule management.
   - Configure network interfaces for traffic monitoring.
   
2. **Rule Management:**
   - Create custom rules or use predefined rule sets for intrusion detection.
   
3. **Logging and Reporting:**
   - Configure logging options to store detected intrusions.
   - Set up reporting mechanisms for analyzing intrusion patterns.
   
4. **Monitoring and Analysis:**
   - Monitor network traffic using Snort.
   - Analyze packet captures using Wireshark for deeper inspection.
   
5. **Alert Handling:**
   - Set up alert mechanisms for real-time notification of detected intrusions.
   
6. **Maintenance and Updates:**
   - Regularly update Snort rules and software for enhanced security.
   - Perform maintenance tasks to ensure smooth operation of the IDS.

This experiment was part of The Learning tasks during The CodeAlpha internship.
