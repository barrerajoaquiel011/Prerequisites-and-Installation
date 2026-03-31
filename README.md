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

1. Search IIS in the Start menu, and open Internet Information Services (IIS) Manager as Administrator.
</p>
<img width="1753" height="1026" alt="Screenshot 2026-03-29 202701" src="https://github.com/user-attachments/assets/1a6b0064-d309-4105-9829-73debe9de9b3" />

2. Select the server on the left panel.
</p>
<img width="653" height="209" alt="Screenshot 2026-03-29 203732" src="https://github.com/user-attachments/assets/28900b10-f3cf-4de1-9a7a-145a67aed5b1" />

3. Open PHP Manager.
</p>
<img width="1753" height="1026" alt="Screenshot 2026-03-29 203803" src="https://github.com/user-attachments/assets/021b80d5-7524-4568-af90-98f36ebd64e7" />

4. Click:
Register new PHP version<br />
</p>
<img width="235" height="41" alt="Screenshot 2026-03-29 204028" src="https://github.com/user-attachments/assets/f51a0dfe-d8b1-482d-ad07-8957d21cedbb" />

5. Click the three dots.
</p>
<img width="762" height="330" alt="Screenshot 2026-03-29 204233" src="https://github.com/user-attachments/assets/30586e59-1667-47e1-83d5-025a0c379834" />

6. In the C Drive open the PHP folder.
</p>
<img width="931" height="459" alt="Screenshot 2026-03-29 204302" src="https://github.com/user-attachments/assets/c53c2f84-5ebd-4a10-a60e-d8bed7f4a23f" />

7. Doble click → php-cgi
</p>
<img width="930" height="464" alt="Screenshot 2026-03-29 204326" src="https://github.com/user-attachments/assets/f1f5bbbd-8bfd-4ad4-a6f8-95cd8fae1260" />

8. Browse to: <br />
C:\PHP\php-cgi.exe<br />
</p>
<img width="771" height="326" alt="Screenshot 2026-03-29 204340" src="https://github.com/user-attachments/assets/b62c19f6-895f-44b7-a4ce-c6e4d5586bee" />

9. Click OK.
</p>

<h2>Step 11 — Restart IIS</h2>

1. In IIS Manager, select the server.
</p>
<img width="430" height="273" alt="Screenshot 2026-03-29 210022" src="https://github.com/user-attachments/assets/99f757c9-3f19-47f2-9994-2139b0a8fb51" />

2. On the right panel click:<br />
Stop<br />
</p>
<img width="297" height="239" alt="Screenshot 2026-03-29 210051" src="https://github.com/user-attachments/assets/5a259e6b-95b9-42e7-b49c-dedb935affbc" />

3. Then click:<br />
Start<br />
</p>
<img width="294" height="241" alt="Screenshot 2026-03-29 210109" src="https://github.com/user-attachments/assets/a42526c4-6b64-4871-a155-ebcf2bbf63cd" />

This reloads the web server.
</p>

<h2>Step 12 — Install osTicket</h2>

1. Open the osTicket-Installation-Files folder.
</p>
<img width="114" height="127" alt="Screenshot 2026-03-30 011751" src="https://github.com/user-attachments/assets/d72bb74c-7890-4110-9d40-93c3f17ef028" />

2. Locate the file:<br />
osTicket-v1.15.8.zip<br />
</p>
<img width="937" height="386" alt="Screenshot 2026-03-30 011641" src="https://github.com/user-attachments/assets/540e5353-4e49-4e2f-8aa8-b4d9a176206a" />

3. Extract the ZIP file.
</p>
Right click the file, them click Extract All...
<img width="432" height="319" alt="Screenshot 2026-03-30 013956" src="https://github.com/user-attachments/assets/b8ab4f2b-3f84-4879-8b76-ed6e519ceb7d" />
Browse to the default file displayed → and click Extract.
<img width="534" height="418" alt="Screenshot 2026-03-30 013520" src="https://github.com/user-attachments/assets/13b39571-cd48-4fa9-af4d-5f06de3090a0" />


4. Open the extracted folder.
</p>
<img width="218" height="46" alt="Screenshot 2026-03-30 012446" src="https://github.com/user-attachments/assets/b0310952-eef0-4b1b-96c6-f9dcc1ca8667" />

5. Copy the folder named:<br />
upload<br />
</p>
<img width="187" height="94" alt="Screenshot 2026-03-30 012511" src="https://github.com/user-attachments/assets/2b3f780d-193b-47b8-99ac-a7bf033c1513" />

6. Navigate to:<br />
C:\inetpub\wwwroot <br />
</p>
Right click the File Explorer icon on the taskbar (the yellow folder icon shown in the screenshot).  <br />
<img width="430" height="197" alt="Screenshot 2026-03-30 012707" src="https://github.com/user-attachments/assets/b0eee302-7a88-425f-809a-1fac2cc60dd2" />
Double-click on the Local Disk (C:) drive.  <br />
<img width="213" height="36" alt="Screenshot 2026-03-30 012826" src="https://github.com/user-attachments/assets/3fd7134e-d756-4523-a05d-0b016b55df5c" />
Double-click the inetpub folder  <br />
<img width="114" height="37" alt="Screenshot 2026-03-30 012834" src="https://github.com/user-attachments/assets/0b381699-0807-4f4f-a0da-ebe7c2296047" />
Inside the inetpub folder double-click wwwroot  <br />
<img width="127" height="34" alt="Screenshot 2026-03-30 012853" src="https://github.com/user-attachments/assets/aabc036e-102e-4ab9-a2ad-16229d7abf17" />

7. Paste the folder there.
</p>
<img width="1732" height="1001" alt="Screenshot 2026-03-30 013033" src="https://github.com/user-attachments/assets/330d8a27-5a88-4baa-b28a-6d35b9d7548f" />

8. Rename the folder from: upload<br />
to: osTicket<br />
</p>
Right click on the upload folder → click Rename <br />
Type the new name: <br />
osTicket <br />
</p>
<img width="189" height="43" alt="Screenshot 2026-03-30 013211" src="https://github.com/user-attachments/assets/69cea62e-b561-4389-b742-297a3075a571" />

<h2>Step 13 — Enable Required PHP Extensions</h2>

1. Open IIS Manager.  <br />
</p>
<img width="653" height="522" alt="Screenshot 2026-03-30 171911" src="https://github.com/user-attachments/assets/e5c6b69c-7d42-4d7f-b6be-8311a2aedd09" />

2. Navigate to: <br />
Sites → Default Web Site → osTicket <br />
</p>
<img width="297" height="155" alt="Screenshot 2026-03-30 172609" src="https://github.com/user-attachments/assets/d9ce329e-af29-410d-b191-e38bac1e7abb" />

3. In the right side under Manage Folder click: Browse*:80 (http) to launch the osTicket website. <br />
</p>
<img width="244" height="107" alt="Screenshot 2026-03-30 175156" src="https://github.com/user-attachments/assets/5181e724-d115-4823-a7ae-efdfefd99c8e" />

4. Go back to IIS and Double-click PHP Manager. <br />
</p>
<img width="118" height="109" alt="Screenshot 2026-03-30 173210" src="https://github.com/user-attachments/assets/08e40ac8-e8c8-46f1-8bae-3db1da9ae8bc" />

5. Under PHP Extensions click: <br />

Enable or disable an extension <br />
</p>
<img width="483" height="194" alt="Screenshot 2026-03-30 173513" src="https://github.com/user-attachments/assets/777b8ec0-e05a-46b9-b967-0795c11d5ac8" />

6. Look for and enable the following extensions: <br />

php_imap.dll <br />
<img width="396" height="88" alt="Screenshot 2026-03-30 174305" src="https://github.com/user-attachments/assets/8c331d22-b20a-4cb0-9904-3aa9089ec111" />
</p>
php_intl.dll <br />
<img width="383" height="84" alt="Screenshot 2026-03-30 174342" src="https://github.com/user-attachments/assets/4a4be94c-c8ea-498c-9e0d-f9da23778775" />
</p>
php_opcache.dll <br />
<img width="408" height="87" alt="Screenshot 2026-03-30 174428" src="https://github.com/user-attachments/assets/92248841-279a-4b44-9ae2-7b575d637390" />
</p>

7. Refresh the osTicket webpage.  <br />
</p>
<img width="1747" height="1043" alt="Screenshot 2026-03-30 180417" src="https://github.com/user-attachments/assets/fe81fe64-77c3-4adf-8302-1a4aaa945003" />

<h2>Step 14 — Configure osTicket Settings</h2>

1. Rename the configuration file: <br />

→ Open File Explorer <br />
<img width="194" height="51" alt="Screenshot 2026-03-30 182925" src="https://github.com/user-attachments/assets/83e56cd7-45c7-4791-b5e0-82d5f16032c8" />
</p>
→ In the address bar at the top, paste or browse to: C:\inetpub\wwwroot\ <br />
<img width="796" height="278" alt="Screenshot 2026-03-30 183014" src="https://github.com/user-attachments/assets/fdfca676-2a4d-46e7-a1d5-f827c03868de" />
</p>
→ Double-click the osTicket folder <br />
<img width="159" height="38" alt="Screenshot 2026-03-30 183124" src="https://github.com/user-attachments/assets/8f154822-2323-408a-a72a-37227cb6e7a6" />
</p>
→ Open the folder name: Include <br />
<img width="149" height="33" alt="Screenshot 2026-03-30 183221" src="https://github.com/user-attachments/assets/303b1b39-9e29-4c59-9fab-818dd53b24c5" />
</p>
→ Locate the configuration file named: ost-sampleconfig.php <br />
<img width="229" height="37" alt="Screenshot 2026-03-30 183402" src="https://github.com/user-attachments/assets/d31672a8-5650-4113-bf29-9f9075199b3d" />
</p>
→ Right-click on ost-sampleconfig.php and click rename <br />
<img width="418" height="43" alt="Screenshot 2026-03-30 191742" src="https://github.com/user-attachments/assets/691417df-3448-45e1-98ce-79db82b3673e" />
</p>
→ Change the name to: ost-config.php <br />
<img width="213" height="33" alt="Screenshot 2026-03-30 192014" src="https://github.com/user-attachments/assets/b0b5c495-f6ad-4905-a2de-e56f0328cc87" />
</p>

2. Right-click the file
</p>
→ Properties <br />
</p>
<img width="246" height="46" alt="Screenshot 2026-03-30 193230" src="https://github.com/user-attachments/assets/84c66e4a-f067-4a83-b128-0f5854b0a8ad" />
→ Security <br />
<img width="293" height="103" alt="Screenshot 2026-03-30 193536" src="https://github.com/user-attachments/assets/5dc5a830-b9f8-4672-82b5-4da5e9a7c010" />
</p>
→ Advanced <br />
<img width="281" height="174" alt="Screenshot 2026-03-30 193654" src="https://github.com/user-attachments/assets/9149c8d9-be42-49e7-aa6d-d039304a7d98" />
</p>

3. Disable Inheritance.
</p>
<img width="376" height="149" alt="Screenshot 2026-03-30 194332" src="https://github.com/user-attachments/assets/c6cf19c1-a238-4b49-bd8f-1ce326575fa7" />

4. Remove existing permissions.
</p>
<img width="793" height="379" alt="Screenshot 2026-03-30 194541" src="https://github.com/user-attachments/assets/6d5be81d-931d-4b58-91a5-bd5e845d630f" />

5. Add a new permission:
→ Click add <br />
<img width="127" height="43" alt="Screenshot 2026-03-30 194627" src="https://github.com/user-attachments/assets/b5ae57c4-e9f5-4009-bd2f-e43b7f7ffdb4" />
</p>
→ Select a principal <br />
<img width="176" height="46" alt="Screenshot 2026-03-30 194650" src="https://github.com/user-attachments/assets/f04fc3bd-e053-4637-8036-45cc17787640" />
</p>
→ Everyone → Check Names → Ok <br />
<img width="676" height="164" alt="Screenshot 2026-03-30 195326" src="https://github.com/user-attachments/assets/53c7f689-818d-4886-9118-a4b9f5d4f9c9" />
</p>
→ Full Control <br />
<img width="326" height="233" alt="Screenshot 2026-03-30 195507" src="https://github.com/user-attachments/assets/dd51025e-64c8-4363-9922-4c660e9ccbd8" />
</p> 
→ Apply → Ok <br />
<img width="1102" height="476" alt="Screenshot 2026-03-30 195930" src="https://github.com/user-attachments/assets/8f9f9af7-bb9f-4de3-8a0c-7ab19c610547" />
</p> 

<h2>Step 15 — Create the osTicket Database</h2> 

1. Install HeidiSQL from the installation files folder.
</p>
<img width="384" height="152" alt="Screenshot 2026-03-30 203224" src="https://github.com/user-attachments/assets/29da3af3-8f5a-4099-95c7-16cef9104fae" />

2. Click I accept the agreement → Next → Next → Next → Next → Install
<img width="890" height="289" alt="Screenshot 2026-03-30 204213" src="https://github.com/user-attachments/assets/24a84b0d-ce49-4443-a7ab-a0582462f40e" />
→ Finnish
<img width="881" height="664" alt="Screenshot 2026-03-30 204225" src="https://github.com/user-attachments/assets/6a48dad8-72f9-41b8-9384-43589575e1c3" />

3. Open HeidiSQL, and click New
</p>
<img width="117" height="55" alt="Screenshot 2026-03-30 204526" src="https://github.com/user-attachments/assets/7c79b48f-858a-46b8-9bc3-bbdb5ebf536a" />

4. Create a new session with the following credentials: <br />
 Username: <br />
 root <br />
</p>
 Password: <br />
 root <br />
</p>
<img width="671" height="672" alt="Screenshot 2026-03-30 204643" src="https://github.com/user-attachments/assets/9d4d9ea2-cf33-48e3-8fe7-434acb2d40a4" />

5. Connect to the session.
</p>
<img width="1458" height="765" alt="Screenshot 2026-03-30 204742" src="https://github.com/user-attachments/assets/af09b217-4655-4433-92cb-a5edf9567211" />

5. Create a new database named osTicket: <br />
Right click → Unnamed → Create new → Database <br />
</p>
<img width="735" height="273" alt="Screenshot 2026-03-30 204838" src="https://github.com/user-attachments/assets/e6118373-74ae-4a70-bbd1-af13475a77fb" />

6. Name it: osTicket → them click ok <br />
</p>
<img width="472" height="299" alt="Screenshot 2026-03-30 205226" src="https://github.com/user-attachments/assets/8017310f-8938-496c-b370-53faa9d4ad31" />
<img width="518" height="349" alt="Screenshot 2026-03-30 205243" src="https://github.com/user-attachments/assets/d24116f9-af4e-4f1d-b18d-a3f397a05e37" />

<h2>Step 16 — Complete the osTicket Web Installer</h2>

1. Back in the osTicket website → Click Continue.
</p>
<img width="921" height="801" alt="Screenshot 2026-03-30 201219" src="https://github.com/user-attachments/assets/91aa4371-dae0-4b45-801f-f5106ffcb56b" />

2. Configure the following:
</p>
System Settings <br />
Admin User <br />
<img width="674" height="781" alt="Screenshot 2026-03-30 202006" src="https://github.com/user-attachments/assets/37c4cb14-7f59-4386-9b09-d3069c735f36" />
</p>
Database Settings <br />
<img width="516" height="422" alt="Screenshot 2026-03-30 211705" src="https://github.com/user-attachments/assets/cef75006-6916-40d3-bf79-1ebb97c7c492" />

3. Click Install Now.
</p>
<img width="923" height="722" alt="Screenshot 2026-03-30 213958" src="https://github.com/user-attachments/assets/5fe91cb2-9a84-41ab-a33f-9ebd75adfb2d" />

4. Refresh the osTicket database
→ right click it, them press refresh <br />
<img width="947" height="790" alt="Screenshot 2026-03-30 214149" src="https://github.com/user-attachments/assets/30b601cc-0dfb-4f94-ab7e-5c7d92cb150c" />

<h2>Step 17 — Access the osTicket System</h2>

Admin login page: <br />
http://localhost/osTicket/scp/login.php
</p>
<img width="1750" height="1020" alt="Screenshot 2026-03-30 215608" src="https://github.com/user-attachments/assets/a3dcacba-e333-4fe3-b64f-be703da61a04" />
<img width="1756" height="1023" alt="Screenshot 2026-03-30 215631" src="https://github.com/user-attachments/assets/8870d7c1-2a34-475a-b153-f50471fdd9f0" />

End user support portal: <br />
http://localhost/osTicket/ <br />
</p>
<img width="1757" height="1024" alt="Screenshot 2026-03-30 215250" src="https://github.com/user-attachments/assets/f81701e6-f1da-45c5-9fd2-2b903a2743e9" />
</p>
