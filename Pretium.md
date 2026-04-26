# Pretium

Investigation Here: [Pretium](https://blueteamlabs.online/home/investigation/pretium-fd15e23ad0)

## What is the full filename of the initial payload file? (4 points)
* **Answer**: INVOICE_2021937.pdf.bat
* Looked through the HTTP objects in wireshark to find and interesting requested URI
## What is the name of the module used to serve the malicious payload? (4 points)
* **Answer**: SimpleHTTPServer
* Looking at the initial download, can see 
## Analysing the traffic, what is the attacker's IP address? (4 points)
* **Answer**: 192.168.1.9
* Through the source address of the downloaded pdf.bat file 
## Now that you know the payload name and the module used to deliver the malicious files, what is the URL that was embedded in the malicious email? (5 points)
* **Answer**: http[:]//192[.]168[.]1[.]9[:]443[:]/INVOICE_2021937[.]pdf[.]bat
## Find the PowerShell launcher string (you don’t need to include the base64 encoded script) (5 points)
* **Answer**: powershell -noP -sta -w 1 -enc
* From following the TCP stream within the pcap
## What is the default user agent being used for communications? (4 points)
* **Answer**: Mozilla/5.0
* Inspected some of the beaconing activity and followed the TCP stream
## You are seeing a lot of HTTP traffic. What is the name of a process where malware communicates with a central server asking for instructions at set time intervals? (4 points)
* **Answer**: beacon
## What is the URI containing ‘login’ that the victim machine is communicating to? (5 points)
* **Answer**: /login/process.php
* Filtered wireshark based on ip.src and ip.dst
## What is the name of the popular post-exploitation framework used for command-and-control communication? (5 points)
* **Answer**: empire
* Did some googling with the beacon information that we have 
## It is believed that data is being exfiltrated. Investigate and provide the decoded password (5 points)
* **Answer**: Y0uthinky0ucAnc4tchm3$$
* Used ```tshark``` to pull icmp data using ```"C:\Program Files\Wireshark\tshark.exe" -r LAB.pcap -Y "ip.src==192.168.1.9 and icmp" -T fields -e data```
## What is the account’s username? (5 points)
* **Answer**: $sec-account
* Placed the output of tshark into Cyberchef and decoded from hex and base64