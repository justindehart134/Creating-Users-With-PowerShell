# DNS
# The Domain Naming System
<p align="center">
  <img width="1460" height="730" alt="image" src="https://github.com/user-attachments/assets/8145d2b1-f155-4221-8f3d-299ec6fb300d" />

</p>

<h1>The use of DNS (Azure)</h1>
This is a tutorial on the use and functionality of the Domain naming System within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 

<h2>What is DNS?</h2>
 The Domain Naming system (DNS) is a distribution system that the internet uses. This system works similar to a phonebook. It is the connection betweeen the IP address and the human readable domain name. For examble the IP address 8.8.8.8 translates to www.Google.com. computers interact and identify each other with IP addresses and humans communicate with names and words. DNS is the translator between the two.

<h2>Why do we need DNS?</h2>
Without DNS the internet would be unuseable for nearly everyone. Everyone would manually have to type out the complex IP address to access their desired website. Imagine instead of typing in "google", you now have to type 8.8.8.8 just to access the homepage. Also, large companies use a vast amount of IP addresses, networks, and data centers gloabally. DNS completley makes the internet user friendly.

<h2>How does it work?</h2>
Like I said before, DNS works like a phonebook. All the cell phone numbers (IP addresses) link to a person (website). When you wish to access a website, you type in the desired website and your device then contacts a DNS server. A DNS server has stored a bunch of IP addresses and the linked website. Just like a phonebook. 

- Step 1

Check the local cache

When you search a domain/website, your device checks the local Cache if it has recently been there. If it has, then it already knows the IP address and it doesn't need to ask any further.

- Step 2

Ask the Local Host Files 

If it’s not already saved in the cache, the system looks in the local hosts file. A local host file on your computer that links domains to their IP address. These entries take priority over regular DNS lookups.


- Step 3

  Ask the Recursive Resolver

If your desired destination wasn't in the cache, your computer sends a DNS query to a recursive DNS resolver

A recursive DNS resolver is a server between the users device and the DNS servers that hold the actual records for domain names. A recursive DNS resolver is a server that helps your device find the IP address of a website you’re trying to visit. It basically does the searching for you.


- Step 4

Ask the Root DNS Server 

The resolver then contacts one of the root DNS servers. Theres are 13 main groups of them around the world. These servers don't have the IP address to every domain/ website but they can direct the resolver to the server that does.

This process akes place every time a user looks anything up. The DNS lookup process is super fast 

- Local cache check takes <1 ms

- Recursive resolver query 1–20 ms

- Root server lookup 20–120 ms total


  <h2>MY DNS Lookup</h2>
IN microsoft Azure I created two virtual machines and ran through the DNS lookup process. 

First off in the virtual machine, I opened Powershell torun commands. The first one I ran was to dislay the local cache DNS 
<img width="1512" height="864" alt="Screenshot 2025-11-09 at 6 06 07 PM" src="https://github.com/user-attachments/assets/f0c834dc-bd17-4749-951a-2fe62867ad78" />

This displayed some recent domains/websites left in the cache with their IP addresses and some more information.

Next I attempted to ping "Mainframe" I was met with an error. This is because within the virtual machine, I did not have a file titled "mainframe" for it to ping 
<img width="1512" height="216" alt="Screenshot 2025-11-09 at 6 14 02 PM" src="https://github.com/user-attachments/assets/0b0a65ff-f837-4f1e-bc12-7e8a9af48602" />
<img width="1512" height="216" alt="Screenshot 2025-11-09 at 6 14 32 PM" src="https://github.com/user-attachments/assets/3aeb1635-1abe-4806-887b-494d81e5d030" />


This is files within the my domain files. Clearly there isnt't a file titled "mainframe" so there wasn't anything within the cache to ping. 
<img width="1512" height="680" alt="Screenshot 2025-11-09 at 6 17 07 PM" src="https://github.com/user-attachments/assets/4871d430-da0b-42ac-acec-876fcb54e627" />


I then created the mainframe file and proceeded to ping the file within powershell.
<img width="1512" height="680" alt="Screenshot 2025-11-09 at 6 18 29 PM" src="https://github.com/user-attachments/assets/22d54199-92d5-496b-acf3-55ec73bbe38a" />
<img width="1512" height="353" alt="Screenshot 2025-11-09 at 6 19 07 PM" src="https://github.com/user-attachments/assets/a639e36c-1a82-4ac7-b33e-6a9d3c48a674" />

Within a cell phone. Your contacts have their name linked with their number. This is the same concept here. The cache has it's files name linked with an IP address. And just like a cell phone, you can adjust things. The mainframe originial IP address of 10.0.0.6,I swapped to 8.8.8.8. Which is Google's IP address. 

<img width="648" height="116" alt="Screenshot 2025-11-09 at 6 20 56 PM" src="https://github.com/user-attachments/assets/595bad1c-387b-4af9-97c7-11a96671c683" />

I then proceeded to ping Mainframe to see what would happen.

<img width="618" height="272" alt="Screenshot 2025-11-09 at 6 21 44 PM" src="https://github.com/user-attachments/assets/16e16751-1008-4494-84e2-0eac7a2840f6" />



Mainframe was correctly pinged. But that isn't the IP new address. Why is that? Remeber the DNS process and wht happens first. The first thing that is searched is the local cache. This promted powershell to ping the old mainframe that was left within the cache. 


Now for me toping the corrected mainframe I needed to flush the DNS cache 


<img width="359" height="156" alt="Screenshot 2025-11-09 at 6 30 53 PM" src="https://github.com/user-attachments/assets/c513f1b6-f9fa-40fb-95ef-17f405fe29ba" />


With the DNS being flushed and reset, I was then able to ping the correct mainframe and IP address

<img width="515" height="263" alt="Screenshot 2025-11-09 at 6 31 35 PM" src="https://github.com/user-attachments/assets/b4ec1410-dea4-4938-87b9-c49a5e86e070" />


<h2>DNS Conclusion</h2>

DNS is what makes the internet useable. Without DNS, to use the internet a user would literally have to type a bunch of IP addresses. 

We went over 

- What is DNS
- How it works
- Why it is used
- How it works 












