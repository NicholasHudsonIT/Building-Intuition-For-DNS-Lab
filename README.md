<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png"/>
</p>

<h1>Building Intuition for DNS Lab</h1>
In this lab tutorial we will be experimenting with DNS to help us have a better understanding of it's functions.<br />

<h2>Environments and Technologies Used</h2>

- VirtualBox (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Deployment and Configuration Steps</h2>
<p>
</p>
<p>
First we will be inspecting DNS A records on the server, <i>A records</i> are "domain name to IP address" maps. We are going to create an A record on our Domain Controller DC-1 for "mainframe" and have it point to DC-1's private IP address (If we try to ping mainframe without setting the DNS record it will not work). When we ping "mainframe" Client-1 is checking the DNS cache, checking its local host file and checking the DNS server. To create an A-record go to the Server Manager > Tools > DNS > DC-1 > Forward Lookup Zones > mydomain.com > right click and create a new A record, title it "mainframe". An A record maps a domain name to the IP address. If we go back to the Client Machine and ping "mainframe" we will get a reply. 
</p>
<br />

<p>
<img src="https://i.imgur.com/xKePr4k.png"/>
</p>
<img src="https://i.imgur.com/yAlrhZw.png"/>
<p>
Now we will change the record address of "mainframe" to 8.8.8.8, if we go back to the client machine it will still ping the old adress even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />
<img src="https://i.imgur.com/KYNmZMz.png"/>
</p>
<img src="https://i.imgur.com/80ARdZu.png"/>
</p>
<p>
Lastly, we will configure a CNAME record that points the host "search" to "www.google.com" If we ping "search" ping will not be able to find the host. we have to go back into the DNS tool on DC-1 and create the CNAME record "search". Once we create the CNAME record is created and we ping "search" it will resolve to www.google.com.
</p>
<br />
<p>
<img src="https://i.imgur.com/LgomfqN.png"/>
</p>
<img src="https://i.imgur.com/NovtDrd.png"/>
<p>
