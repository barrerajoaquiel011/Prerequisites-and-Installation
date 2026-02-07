# Prerequisites-and-Installation<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial demostrates the prerequisites, installation and basic configuration of the open-source help desk ticketing system osTicket. The installation was performed in a cloud based Windows enviroment using Microsof Azure.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL
- PHP

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
1️⃣ Windows 10 Virtual Machine created in Microsoft Azure.
</p>
 <p>
<img width="1821" height="1001" alt="Screenshot 2026-02-06 194306" src="https://github.com/user-attachments/assets/683ede93-101c-483f-91c3-9153d08e9866" />
I created a virtual machine in Microsoft Azure. The VM is currently in an In Execution state, confirming that it is running successfully.
</p>
  <br />
2️⃣ Remote Desktop Connection
</p>
 <p>
<img width="1919" height="1079" alt="Screenshot 2026-02-06 195843" src="https://github.com/user-attachments/assets/3fa2a43a-7171-4da0-a0a1-848416bc5a0f" />
A Remote Desktop connection was successfully established to the virtual machine. The Windows desktop is displayed with the taskbar visible.
</p>
  <br />
3️⃣ IIS Installation
</p>
 <p>
<img width="1436" height="922" alt="Screenshot 2026-02-06 205417" src="https://github.com/user-attachments/assets/73f589f6-f5f2-42d6-9c4e-b3c24d55abe7" />
<img width="1916" height="81" alt="Screenshot 2026-02-06 210730" src="https://github.com/user-attachments/assets/6ee5f8e9-d825-4d90-91fb-5709f48d962d" /> Internet Information Services (IIS) was enabled on the Windows virtual machine to host the web application.
</p>
  <br />
4️⃣ PHP Configuration
</p>
 <p>
<img width="1451" height="941" alt="Screenshot 2026-02-07 105416" src="https://github.com/user-attachments/assets/be1c0544-25cc-40b7-b81b-caa183bdd59e" />
PHP was installed and properly configured in IIS to support the osTicket application.
</p>
  <br />
5️⃣ Database Setup
</p>
 <p>
 <img width="1629" height="1023" alt="Screenshot 2026-02-07 105734" src="https://github.com/user-attachments/assets/38c9ab29-bdfe-4d2d-b89f-27a5360599b9" />
 MySQL was installed and a database was created to store osTicket application data.
 </p>
   <br />
6️⃣ osTicket Installation
</p>
 <p>
<img width="1459" height="944" alt="Screenshot 2026-02-07 104715" src="https://github.com/user-attachments/assets/f4eaab1f-7e55-4164-85e6-5ee7164abe83" />
The osTicket application was installed through the web browser using the configured server environment.
</p>
  <br />
7️⃣ Project Running
</p>
 <p>
<img width="1458" height="940" alt="Screenshot 2026-02-07 105030" src="https://github.com/user-attachments/assets/6ed7a7e1-246d-4444-80cc-1cc5295f27de" />
This screenshot shows osTicket running successfully inside the virtual machine after completing the installation.
</p>
  <br />
<h2>Conclusion</h2>
The virtual machine was successfully deployed in Azure, accessed via Remote Desktop, and configured to run the osTicket application.
