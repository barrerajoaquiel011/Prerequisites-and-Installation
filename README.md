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
<img width="1821" height="947" alt="Screenshot 2026-03-21 194259" src="https://github.com/user-attachments/assets/5efedc53-b0db-4f3d-8005-2da5b517a1bd" />

2. Click the virtual machine named:
osticket-vm </p>
<img width="1826" height="954" alt="Screenshot 2026-03-21 194324" src="https://github.com/user-attachments/assets/69182024-aeb8-4046-acca-bedfbe89d688" />

3. Copy the Public IP Address of the Virtual Machine. </p>
<img width="1821" height="957" alt="Screenshot 2026-03-21 195119" src="https://github.com/user-attachments/assets/8231dcbf-f458-4080-a2ba-46653ba087ef" />

4. Click Start Menu, the windows sign in the task bar and search "Remote Desktop Connection" </p>
<img width="1919" height="1079" alt="Screenshot 2026-03-21 200435" src="https://github.com/user-attachments/assets/f64b6493-0d5f-492c-aa81-bc6ab1e503df" />

5. Click [OPEN] </p>
<img width="647" height="372" alt="Screenshot 2026-03-21 200556" src="https://github.com/user-attachments/assets/faeb8e2a-650f-4a80-b4d8-919275fba64b" />

6. Paste the Public IP Address from the Azure VM:<br />
Computer: 172.184.243.44 </p>
<img width="615" height="374" alt="Screenshot 2026-03-21 201022" src="https://github.com/user-attachments/assets/8a12b8ab-25f6-4b24-add0-acef131f92df" />

7. Click Connect </p>
<img width="609" height="375" alt="Screenshot 2026-03-21 201043" src="https://github.com/user-attachments/assets/5cfb32cf-89a5-4032-9480-a70eb446677f" />

8. Enter the login credentials: </p>
Username: labuser<br />
Password: osTicketPassword$$ </p>

9. Click OK to log into the Windows virtual machine. </p>
<img width="1635" height="1021" alt="Screenshot 2026-03-21 203140" src="https://github.com/user-attachments/assets/10973ad5-765b-474f-882a-ea67d946bdab" />

<h2>Step 3 — Download the osTicket Installation Files</h2>
Inside the virtual machine: </p>

1. Open a web browser and access the URL containing the osTicket installation files (.zip). </p>
<img width="1818" height="1000" alt="Screenshot 2026-03-24 175911" src="https://github.com/user-attachments/assets/5cdab939-06ba-474f-b699-f7c0ddb77b92" />

2. Click the link and download the file: </p>
<img width="505" height="115" alt="Screenshot 2026-03-24 182037" src="https://github.com/user-attachments/assets/3a296c0f-306c-4ff2-9019-6166af69ce3c" />

3. osTicket-Installation-Files.zip </p>
<img width="1628" height="490" alt="Screenshot 2026-03-24 182149" src="https://github.com/user-attachments/assets/a8a9b00f-4458-426f-9b2a-4c5e428b73b4" />

4. Save the file to the Desktop by dragging it out of the Downsloads folder. </p>
<img width="1636" height="1024" alt="Screenshot 2026-03-24 182541" src="https://github.com/user-attachments/assets/996cce9d-9c4d-44b8-8fb7-e12073f1a436" />

5. Right-click the ZIP file.</p>
<img width="584" height="716" alt="Screenshot 2026-03-24 183417" src="https://github.com/user-attachments/assets/695d1373-d252-449b-a575-9c6711d7084e" />

6. Click Extract All.</p>
<img width="1627" height="1023" alt="Screenshot 2026-03-24 182930" src="https://github.com/user-attachments/assets/26625dae-e6a0-43a4-a65a-9748d2f6b116" />

7. Extract the folder to the Desktop. </p>
After extraction, the folder should be named:<br />
osTicket-Installation-Files</p>
<img width="1638" height="1034" alt="Screenshot 2026-03-24 183710" src="https://github.com/user-attachments/assets/b2b32945-f7cf-42dd-9354-5c57a1f4731c" />

<h2>Step 4 — Install Internet Information Services (IIS) with CGI</h2>

1. Click the Start Menu.
</p>
<img width="1017" height="1020" alt="Screenshot 2026-03-24 190538" src="https://github.com/user-attachments/assets/834659bc-2926-4691-b4a6-36e67d3ff081" />

3. Search for:</p>
Control Panel
</p>
<img width="1631" height="1020" alt="Screenshot 2026-03-24 190450" src="https://github.com/user-attachments/assets/bf3e359a-83f0-4478-8caf-24772f8ce713" />

4. Click Programs → Uninstall a program.
</p>
<img width="1682" height="955" alt="Screenshot 2026-03-24 191834" src="https://github.com/user-attachments/assets/27a4ebb1-2e3d-4d02-8e8a-0d99bd7afb61" />

5. Turn Windows features on or off.
</p>
<img width="307" height="311" alt="Screenshot 2026-03-24 191934" src="https://github.com/user-attachments/assets/e4cb2425-e44d-431f-9c1b-fcacb908cc80" />

6. Enable the following features:</p>
</p>
Internet Information Services<br />
World Wide Web Services<br />
Application Development Features<br />
CGI</p>
<img width="823" height="746" alt="Screenshot 2026-03-24 192933" src="https://github.com/user-attachments/assets/d449eb52-00aa-4b92-bea3-f3175f9a2c5f" />

6. Click OK.
</p>
<img width="738" height="189" alt="Screenshot 2026-03-24 193019" src="https://github.com/user-attachments/assets/e678273b-9282-4268-9953-ec1ef1c0ad28" />
<img width="965" height="870" alt="Screenshot 2026-03-24 193156" src="https://github.com/user-attachments/assets/99603a40-6c50-4d96-a563-784e9b4fed9d" />

Windows will install IIS automatically. </p>

<h2>Step 5 — Install PHP Manager for IIS</h2>

1. Open the osTicket-Installation-Files folder.
</p>
<img width="1180" height="341" alt="Screenshot 2026-03-24 195450" src="https://github.com/user-attachments/assets/94af70b6-a43f-4668-985d-cc3946d746ac" />

2. Locate the installer: </p>
PHPManagerForIIS_V1.5.0.msi<br />
</p>
<img width="968" height="371" alt="Screenshot 2026-03-24 195724" src="https://github.com/user-attachments/assets/56f130e1-0a15-4aa8-8631-83e9244ebef7" />

3. Double-click the file.
</p>
<img width="787" height="646" alt="Screenshot 2026-03-24 200223" src="https://github.com/user-attachments/assets/41eda009-e2a9-4ac3-8d14-656f235f6275" />

4. Follow the installation wizard. </p>
License Agreement → I Agree → Next><br />
</p>
<img width="789" height="637" alt="Screenshot 2026-03-24 200239" src="https://github.com/user-attachments/assets/520b698f-dc3f-4241-89e6-7aee9a2f08da" />

5. Click Close after installation completes.
</p>
<img width="786" height="649" alt="Screenshot 2026-03-24 200255" src="https://github.com/user-attachments/assets/8324d1e7-79b9-49cf-8d22-60874a3f685e" />

<h2>Step 6 — Install the IIS Rewrite Module</h2>

1. In the osTicket-Installation-Files folder, locate:<br />
rewrite_amd64_en-US.msi<br />
</p>
<img width="1733" height="956" alt="Screenshot 2026-03-24 202829" src="https://github.com/user-attachments/assets/e7642bba-bb66-47ea-8d91-8ed2819259b4" />

2. Double-click the installer.
</p>
<img width="768" height="596" alt="Screenshot 2026-03-24 204926" src="https://github.com/user-attachments/assets/d4b51564-b458-41ec-8976-e4d2f84852b5" />

3. Check the box [✅] Accept the terms in the License Agreement, and click Install.
</p>
<img width="773" height="606" alt="Screenshot 2026-03-24 205115" src="https://github.com/user-attachments/assets/0d628007-1b86-4a05-bdd4-1d41d2029e99" />

4. Click Finish after installation completes.
</p>
<img width="773" height="604" alt="Screenshot 2026-03-24 205204" src="https://github.com/user-attachments/assets/3cd4885f-c18b-46a8-be43-ca2ebab152fa" />

<h2>Step 7 — Install PHP</h2>
1. Open File Explorer.
</p>
<img width="1834" height="1076" alt="Screenshot 2026-03-25 103414" src="https://github.com/user-attachments/assets/2d834dc6-9f13-46df-89cb-e5cef7e4233d" />

2. Navigate to the C: drive.
</p>
<img width="1171" height="827" alt="Screenshot 2026-03-25 103559" src="https://github.com/user-attachments/assets/725aeef1-0672-47a1-9daf-4582c81bb264" />

3. To create a new folder right click inside the C: drive

→ New  > →Folder <br />
</p>
<img width="705" height="534" alt="Screenshot 2026-03-25 103717" src="https://github.com/user-attachments/assets/f24ae22b-4064-418a-8fc6-7563d330a124" />

4. Name the folder:
PHP
</p>
<img width="145" height="41" alt="Screenshot 2026-03-25 103848" src="https://github.com/user-attachments/assets/264de19a-b580-4641-af52-97ea3041a08e" />

5. Open the osTicket-Installation-Files folder.
</p>
<img width="1029" height="517" alt="Screenshot 2026-03-25 104933" src="https://github.com/user-attachments/assets/66bce061-3a4a-4373-985d-ff5082950d96" />

6. Locate the file:
php-7.3.8-nts-Win32-VC15-x86.zip<br />
</p>
<img width="940" height="31" alt="Screenshot 2026-03-25 105009" src="https://github.com/user-attachments/assets/e788a98e-a063-4fef-952a-61316777573d" />

7. Right-click the file.
</p>
<img width="770" height="622" alt="Screenshot 2026-03-25 105127" src="https://github.com/user-attachments/assets/05e71b3f-48bb-478b-8f41-2c8fd6eb0361" />

8.Click Extract All.
</p>
<img width="227" height="44" alt="Screenshot 2026-03-25 110251" src="https://github.com/user-attachments/assets/9be46932-f185-4448-a23b-4c03d0b7c6d1" />

9. Extract the contents to C:\PHP:
Browse...  →C: drive →PHP →Select Folder →Extract.<br />
</p>
<img width="125" height="54" alt="Screenshot 2026-03-25 105523" src="https://github.com/user-attachments/assets/22f7c5b2-13a1-4e30-9167-6a9436108ef4" />

<h2>Step 8 — Install Microsoft Visual C++ Redistributable</h2>

1. In the installation files folder, locate:
 VC_redist.x86.exe<br />
 </p>
<img width="238" height="53" alt="Screenshot 2026-03-25 112212" src="https://github.com/user-attachments/assets/48208cfe-271e-4836-9e8e-700216df0ff7" />
 
2. Double-click the file.</p>

3. Agree to the license terms... , and Click Install.
</p>
<img width="717" height="455" alt="Screenshot 2026-03-25 112345" src="https://github.com/user-attachments/assets/e7923e85-3144-4247-a8d9-c4a2d0ec92e4" />

4. Wait for the installation to complete.
</p>
<img width="717" height="430" alt="Screenshot 2026-03-25 112531" src="https://github.com/user-attachments/assets/d52e8b4b-aa58-4875-890e-4487d709e2b1" />

<h2>Step 9 — Install MySQL Server</h2>

1. In the installation files folder, locate:
mysql-5.5.62-win32.msi<br />
</p>
<img width="1040" height="420" alt="Screenshot 2026-03-29 193901" src="https://github.com/user-attachments/assets/9f10161a-c884-4c58-a570-82da9be8eb76" />

2.Double-click the installer.
</p>
<img width="768" height="601" alt="Screenshot 2026-03-29 193954" src="https://github.com/user-attachments/assets/a7aa58e2-6d57-4b56-95d1-6961d05075da" />

3.Select Typical Setup. 
</p>
<img width="454" height="359" alt="Screenshot 2026-03-29 195633" src="https://github.com/user-attachments/assets/278a02ab-2ee2-43af-8ae0-6260a6193d76" />

4. After installation finishes, start the Configuration Wizard.
</p>
<img width="749" height="563" alt="Screenshot 2026-03-29 194226" src="https://github.com/user-attachments/assets/a9daec72-cbab-433e-a796-317eaf62f559" />

5. Select:
Standard Configuration<br />
</p>
<img width="753" height="571" alt="Screenshot 2026-03-29 194303" src="https://github.com/user-attachments/assets/82bf95a8-20c9-4556-a4ff-424d058ecd05" />

6. Configure the database credentials.

Username:<br />
root<br />
Password:<br />
root <br />
</p>
<img width="456" height="345" alt="Screenshot 2026-03-29 200654" src="https://github.com/user-attachments/assets/e01ced1b-4997-4613-b4ca-6549c57828e5" />

7. Complete the configuration.
</p>
<img width="744" height="571" alt="Screenshot 2026-03-29 195024" src="https://github.com/user-attachments/assets/19e209d5-38ca-45ce-8957-6e16c77f75e8" />


<h2>Step 10 — Register PHP in IIS</h2>
Open Internet Information Services (IIS) Manager as Administrator.
Select the server on the left panel.
Open PHP Manager.
Click:
Register new PHP version
Browse to:
C:\PHP\php-cgi.exe
Click OK.

<h2>Step 11 — Restart IIS</h2>
In IIS Manager, select the server.
On the right panel click:
Stop
Then click:
Start

This reloads the web server.

<h2>Step 12 — Install osTicket</h2>
Open the osTicket-Installation-Files folder.
Locate the file:
osTicket-v1.15.8.zip
Extract the ZIP file.
Open the extracted folder.
Copy the folder named:
upload
Navigate to:
C:\inetpub\wwwroot
Paste the folder there.
Rename the folder from:
upload

to

osTicket

<h2>Step 13 — Enable Required PHP Extensions</h2>
Open IIS Manager.
Navigate to:
Sites → Default Web Site → osTicket
Double-click PHP Manager.
Click:
Enable or disable an extension
Enable the following extensions:
php_imap.dll
php_intl.dll
php_opcache.dll
Refresh the osTicket webpage.

<h2>Step 14 — Configure osTicket Settings</h2>
Rename the configuration file:

From

C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

To

C:\inetpub\wwwroot\osTicket\include\ost-config.php
Right-click the file → Properties → Security.
Disable Inheritance.
Remove existing permissions.
Add a new permission:
Everyone → Full Control

<h2>Step 15 — Create the osTicket Database</h2>
Install HeidiSQL from the installation files folder.
Open HeidiSQL.
Create a new session with the following credentials:

Username

root

Password

root
Connect to the session.
Create a new database named:
osTicket

<h2>Step 16 — Complete the osTicket Web Installer</h2>
Open a browser inside the VM.
Navigate to:
http://localhost/osTicket
Click Continue.
Configure the following:

Helpdesk Name

My Helpdesk

Default Email

admin@helpdesk.com

Database Name

osTicket

Database Username

root

Database Password

root
Click Install Now.

<h2>Step 17 — Access the osTicket System</h2>

Admin login page

http://localhost/osTicket/scp/login.php

End user support portal

http://localhost/osTicket/

<h2>Step 18 — Cleanup</h2>
Delete the setup folder:
C:\inetpub\wwwroot\osTicket\setup
Change permissions for the configuration file:
C:\inetpub\wwwroot\osTicket\include\ost-config.php

Set permissions to:

Read Only
