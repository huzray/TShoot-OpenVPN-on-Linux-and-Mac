Most OpenVPN issues can be resolved with the suggestions below.

If you're new to the platform, you can follow this article to familiarize yourself with OpenVPN.

 

Although using OpenVPN has advantages, we recommend that beginners use the Attackbox, as this solution comes with all the necessary tools and no VPN connection is required.

 

Before troubleshooting, please update and upgrade your OS to ensure the issues aren't caused by old software. If you are using Linux, please make sure you use the terminal and not the network manager. Please refer to the OpenVPN room if you are unsure how to do this. 


​Please also ensure that your openVPN configuration file is up to date; you can do this by heading over to your "access" page, clicking on "regenerate", waiting 2 minutes and downloading it again.
​
​



​These steps may not work for WLS/ WSL 2. We would recommend that you use a Virtual Machine with Virtual Box or VMware if you continue to have issues after following these steps

 

 

First troubleshooting steps:
To resolve issues you may be experiencing with OpenVPN, please attempt the following steps:

 

First, close any external VPN services (such as NordVPN, ProtonVPN or Windscribe); the only VPN service you should be running is OpenVPN.

 

If that does not work, or you do not have any external VPN services running, please try running this command in your terminal:

 

sudo killall openvpn
 

This command will stop all active instances of the OpenVPN service, including any running in the background or ones that have not shut down properly. 

 

When prompted, enter your password; you should not see any output after running the command; just re-run the OpenVPN initialization command (sudo openvpn filename.ovpn) and try running the following command in your terminal:

 

curl 10.10.10.10/whoami
 

If an IP address (starting with 10.x.x.x) is returned, you are connected and ready to continue learning.

 

• If the issue persists, even though you have tried the previous steps, please try turning down the maximum bytes you send across the network. To do this, execute the following command in a separate terminal window:

 

sudo ip link set dev tun0 mtu 1200
 

 

Known issues:
 

Issue:
When configuration files are generated with formatting issues, OpenVPN will fail with an error similar to the following if yours has been generated with errors:

 
Mon Jun 15 22:28:35 2020 Cannot load inline certificate file
Mon Jun 15 22:28:35 2020 Exiting due to fatal error
 

Solution:
To fix this, switch VPN servers and press "Regenerate". For example, suppose you were on EU-Regular-1. In that case, you should swap to EU-Regular-2 and press "Regenerate" like below:

 

Regenerating OpenVPN onfiguration File
 

Please wait 2 minutes before pressing "Download My Configuration File." This will allow enough time for a new configuration file to be generated for you. 

 

 

Issue:
You're getting a 404 error "lost in the matrix" when downloading your configuration file, or your config file is empty.

 


 

Solution:
Please refresh your browser, regenerate your configuration file and wait a few minutes before downloading it again.

 

Issue:
You're not receiving reverse shells or Metasploit exploits are not creating sessions.

 

Solution:
 

This is often caused by incorrect settings (so double-check this first) or by using a VM running the VPN on your host machine. If the VPN is connected to your host and the VM is connected through the host, then you have a route into the network and can access machines: VM -> Host -> TryHackMe Network. Your reverse shells don't know about that extra step, though: as far as they're concerned, your TryHackMe IP belongs to your host -- not the VM. When the reverse shell is sent, it gets sent back to the host but goes no further -- it has no reason to because it's already reached its destination. 

 

If none of the above solutions fixed your issue, please try running the script below.

 

Troubleshooting script:
Download the TryHackMe OpenVPN Troubleshooting script directly to your Linux machine

In your Linux terminal, make the script executable with chmod +x <path-to-script>. If you downloaded the script to your Downloads folder, this would be chmod +x ~/Downloads/thm-troubleshoot. 

Run the script by typing sudo followed by the path to the script into your terminal and pressing enter. If the script is in your downloads, it will be the following command: sudo ~/Downloads/thm-troubleshoot. 

The script will instruct you on how to proceed from there.

 

If you continue to experience issues after trying these steps, email us at support@tryhackme.com or open a ticket via our chatbot.
