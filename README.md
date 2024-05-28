# Netcat_ReverseShell
Aware of the power of the terminal, we want to take control of it remotely to simulate an attack capable of extracting all sensitive data stored locally and accessible from the computer. To do this, it is possible to use the Netcat protocol, which allows remote control of a machine's terminal. Since directly attacking a machine is very difficult due to firewalls protecting network access, we have chosen to exploit the greater freedom firewalls allow for outbound traffic to external networks. Indeed, it is difficult for external requests to reach the personal computer, but it is relatively easy for the computer to connect outside the network.

To exploit this vulnerability, we use a DigiSpark USB stick, which simulates a keyboard, to automatically send a connection request to a web page hosted on a Linux system. Once the connection is established, the web page loads a script that is executed on the computer's terminal. This script sends a connection request to the Linux device, allowing us to take control of the terminal remotely. Once we have access to the terminal, we can execute a series of commands to explore the file system, extract sensitive data, and transfer it to our device. This simulation highlights the need to implement stricter security measures, such as limiting physical access to devices, using multi-factor authentication, and advanced firewall configurations to also monitor outbound traffic. Through this demonstration, we aim to raise awareness among users about the importance of protecting the terminal and the critical information it can reveal if compromised.

### PHASE 0 - PREPARATION
1. Load an HTML file with a script generated using the Reverse Shell website, specifying the IP address of the attacking device and the port on which you want to establish the Netcat connection. This file constitutes the web page to be published on Linux and should be loaded into the correct folder: "C:/var/www/html".
2. To send useful information accessible to the attacking computer, set up credentials on the Webhook site, which will generate a link to which the attacked computer will send readable information to the attacker.
3. Modify Script 1 so that the information is sent to the correct link (generated on Webhook) and load it onto DigiSpark 1.
4. Load Script 2 onto DigiSpark 2.

### PHASE 1 - ENTER THE NETWORK AND DISABLE WINDOWS DEFENSE
1. Modify Script 1 so that the information is sent to the correct link (generated on Webhook) and load it onto DigiSpark 1.
2. Insert DigiSpark 1 into the Windows computer and wait for it to complete the script (about 30 seconds).
3. Remove DigiSpark 1.
4. Connect to the same network as the Windows computer using the credentials received on Webhook.

### PHASE 2 - REVERSE SHELL
1. Change your IP address within the network if necessary (the IP address must be the same as the one loaded onto Script 2 within DigiSpark 2).
2. Launch the website on Linux and ensure it functions correctly.
3. Start listening on the port where you expect the connection request.
4. Insert DigiSpark 2 into the attacked computer (Windows) and wait for it to complete the script (about 30 seconds).
5. Remove DigiSpark 2.

### PHASE 3 - PLAY RESPONSIBLY
If everything has gone as expected, the Linux computer should have access to the terminal of the Windows computer and therefore full access to all functions with administrator privileges. Note that on Windows, the commands executed via Linux through the reverse shell will not be visible, so the attacked user will not see any commands. Use this attack responsibly.
