# osTicket Prerequisites and Installation<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

This tutorial explains how to install the open-source help desk system osTicket inside a Windows virtual machine hosted in Microsoft Azure.

The process includes creating the Azure virtual machine, installing the required web server components, configuring PHP, installing the database server, and completing the osTicket web installation.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machines
- Remote Desktop
- Internet Information Services
- PHP
- MySQL
- HeidiSQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Windows 10 Virtual Machine
- Internet Information Services (IIS) enabled
- PHP 7.4
- PHP Manager for IIS
- IIS Rewrite Module
- MySQL Server
- osTicket installation files


<h2>Installation Steps</h2>
<h2>Step 1 — Create the Azure Virtual Machine</h2>
1. Open a browser and go to the Azure Portal:
https://portal.azure.com<br />
2. Sign in with your Azure account.
<img width="1919" height="1079" alt="Screenshot 2026-03-18 094742" src="https://github.com/user-attachments/assets/72929599-a43d-4744-b935-1a9b2152a54e" />

3. In the search bar at the top of the portal, type:
Virtual Machines
</p>
<img width="1818" height="989" alt="Screenshot 2026-03-18 100619" src="https://github.com/user-attachments/assets/75c52ff5-5a0e-4bfa-9b94-ef6746e28856" />

4. Click Virtual Machines from the results.
</p>
<img width="1818" height="1002" alt="Screenshot 2026-03-18 101109" src="https://github.com/user-attachments/assets/dcd9b7e0-062e-4972-b4dc-97053ad2f012" />


5. Click Create → Azure Virtual Machine.
</p>
<img width="523" height="170" alt="Screenshot 2026-03-18 101245" src="https://github.com/user-attachments/assets/dab93a78-0c75-4805-814d-d591b8684ab4" />

6. Create a new Resource group.</p>
   Name: osTicket</p>
   <img width="1154" height="445" alt="Screenshot 2026-03-18 103338" src="https://github.com/user-attachments/assets/fd9bacd1-949b-4a1b-b2b4-c76977a452f1" />

7. Under Basics, configure the VM with the following settings:</p>
   VM Name:  osticket-vm</p>
   Image:  Windows 10</p>
      <img width="1817" height="933" alt="Screenshot 2026-03-18 104521" src="https://github.com/user-attachments/assets/06b18e19-78d6-44e8-a2f7-f65284b45c03" />
   Size:  4 vCPUs</p>
   Administrator Username:  labuser</p>
   Administrator Password:  osTicketPassword$$</p>
   <img width="1818" height="933" alt="Screenshot 2026-03-18 104742" src="https://github.com/user-attachments/assets/eac39319-20b9-4373-9221-abc62082fe4d" />
8. Allow the RDP (3389) inbound port, and confirm the Licensing ✅</p>
   <img width="1825" height="946" alt="Screenshot 2026-03-18 104817" src="https://github.com/user-attachments/assets/2d630701-b709-44fe-b7c6-23292ffe49cf" />
9. Click Review + Create, then click Create.</p>
<img width="1827" height="929" alt="Screenshot 2026-03-18 111641" src="https://github.com/user-attachments/assets/119a5697-6d8b-4a2f-8c73-3aec097b0293" />
<img width="1822" height="943" alt="Screenshot 2026-03-18 111954" src="https://github.com/user-attachments/assets/b165f493-9385-4273-bc9a-8bb8c9749459" />
<h2>Step 2 — Connect to the Virtual Machine Using Remote Desktop</h2>
1. After the VM finishes deploying, open the Virtual Machines page.</p>
2. Click the virtual machine named:
osticket-vm
