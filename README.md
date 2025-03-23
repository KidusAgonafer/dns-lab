<p align="center">
  <img src="https://github.com/user-attachments/assets/1554666a-c615-4fde-b915-0890e0964210" alt="Project Logo" width="20%"/>
</p>


# DNS Lab

## **Environments and Technologies Used**
- Microsoft Azure
- Active Directory
  

## **Operating Systems Used**
- Windows 10

## **Objectives**
- Creating and inspecting A-Records
- Understanding DNS cache by observing and deleting DNS cache
- Creating CNAME records

---

## **Implementation Steps**
**A-Records**
- Before diving into A-Records, it's essential to understand how the DNS hierarchy operates. The DNS hierarchy is a distributed system that resolves domain names into IP addresses. It follows a structured process to locate the requested domain efficiently:
  1. Local DNS Cache (Fastest): This is the most efficient method, as it checks for previously resolved domain names stored on the local device.
  2. Local Host file (Faster): If the cache doesn't have the information, the system searches the host file, which can map specific domain names to IP addresses.
  3. DNS server (Slowest): The system queries a DNS server if neither the cache nor the host file can resolve the domain. This process may involve contacting multiple servers, starting with the recursive DNS server, then moving up through the root nameserver, the top-level domain (TLD) server, and finally the authoritative nameserver.
     
- Now we have an understanding of A-Records, log into both DC-1 and Client-1 as your domain admin account. Example: (mydomain.com\jane_admin)
- From Client-1, open PowerShell and attempt to ping the domain name "mainframe." The ping request fails because the system cannot resolve "mainframe" into an IP address. This occurs due to the absence of a record for "mainframe" in the DNS resolution process, meaning the domain name is not mapped to any IP address in the available cache, host file, or DNS server.
- The DNS Cache can be looked up by typing "ipconfig /displaydns"
-  The DNS host file can be seen  by opening the Notepad app and clicking  "run as administrator" option. Once opened click File > Change File option to "All Files".
- Follow the file path ThisPC > Windows(C) > System32 > drivers > etc > hosts . Your screen should have something like below
  ![image](https://github.com/user-attachments/assets/855fe643-b143-40fa-9fc5-97ecb94d8342)
  ![image](https://github.com/user-attachments/assets/a4e2395a-c1b3-4ffb-bae4-511fa7b0cd17)
- The hosts file can be edited to alter the results of commands in the command prompt. For instance, if you go to the command line and type ping tiger, it will produce an error because 'tiger' isn't mapped to any IP address. However, if you modify the hosts file and add the entry 127.0.0.1 tiger (utilizing the loopback interface) the ping will succeed by resolving 'tiger' to your local machine. Make sure the to save the file before retrying ping. 
  ![image](https://github.com/user-attachments/assets/bd7dead0-d012-41ff-8dcb-ed79c87e3a9e)




