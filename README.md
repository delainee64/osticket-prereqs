<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure
- Azure Virtual Machine running Windows OS
- Installation Files within VM (<a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Download All</a>):
  - <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHP Manager for IIS v1.5.0</a>
  - <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">Rewrite Module</a>
  - <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">PHP v7.3.8 NTS</a>
  - <a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view">Microsoft Visual C++ Redistributable</a>
  - <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">MySQL v5.5.62</a>
  - <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a>

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/f046f7a6-a8d4-4ba4-b5e3-f6de83927a5b" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
The first step in creating an osTicketing system is to create a virtual machine (Windows 10) and virtual network within a resource group in Azure. In this photo, you can see the resources created.
</p>
<br />

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/5b8d46e4-8e6a-43f8-a5b5-cead28df1ecc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Next, open the "Remote Desktop Connection" on your device. Using the virtual machine's public IP address, log in to the virtual machine. Once in, access the control panel within the virtual machine and select "Programs" --> "Turn Windows features on or off". First, select "Internet Information Systems" then expand the section and select "World Wide Web Services" and expand that section. Select "Application Development Features" and check "CGI". Then select "Common HTTP Features" and check all of the subsections. Lastly, select and expand "Web Management Tools" and check "IIS Management Console". 
</p>
<p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/0516874e-106d-49bb-b1f8-6e9dc5efb3eb" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
osTicket runs on IIS, so make sure IIS is working before moving forward. Simply access an internet browser and search "127.0.0.1". IIS should appear as it does in the above photo.

Install PHPManagerForIIS_V1.5.0.msi and rewrite_amd64_en-US.msi in your virtual machine.
<br />

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/ab2d19a3-bed8-4446-b7c8-330339baa70a" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<p>
Create the directory C:\PHP
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/f7b3a323-dd3a-46ac-a095-4f3451e58697" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<p>
Download and install "php-7.3.8-nts-Win32-VC15-x86.zip and unzip the contents into C:\PHP.
Download and install "vc_redist.x86.exe" and "mysql-5.5.62-win32.msi". When installing the MySQL server, select a typical setup, standard configuration, and select a password.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/5360f860-e0ee-466b-a73f-4a7f74123e37" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<p>
Open IIS as an admin by right-clicking on ISS and selecting "Run as admin". Select "PHP Manager" --> "Register New PHP Version" and browse for C:\PHP --> "php-cgi" and restart the server.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/9f286af5-4e4c-4bcb-9735-6c47cdc173d6" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<p>
Download and open the file "osTicket-v1.15.8.zip". In another folder window, go to your hard drive and select "inetpub" --> "wwwroot" and then drag the "upload" folder to "wwwroot". Rename "upload" to "osticket". Restart IIS.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/1a4bf340-e11c-4494-8937-ab42a86013e5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Go to IIS, select "Sites" --> "Default Web Site" --> "osTicket" and then click "Browse *:80 (HTTP)" 
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/fc307e2f-0c9c-48c1-9eba-77d904a06ab8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
To enable the recommended prerequisites in osTicket, go back to IIS --> "osTicket" --> "PHP Manager" --> "Enable or Disable an Extension". Then enable php_imap.dll, php_intl.dll, php_opcache.dll. Restart IIS.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/6f25c648-baa1-43aa-b20a-a2378bab86da" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Next, go back to "wwwroot" on your hard drive. "osTicket" --> "include" --> "ost-sampleconfig.php" and rename this file to "ost-config.php". Right click the file and go to "properties" --> "security" --> "advanced" --> "Disable Inheritance" --> "Remove all permissions" --> "Add" --> "Select a principal" and type "everyone" in the text box and check the name. In the next window, check "full control" and apply the changes.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/21128b6a-af05-49e0-8cac-7eeb985343bf" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Go back to osTicket on your browser and click "continue" and fill in the requested information.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/15cdb98f-81af-4946-be5e-086497cb44a1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Install Heidi SQL. Open Heidi SQL and select "New" and enter the password you selected earlier. Right-click "Unnamed" and select "New" --> "Database" and name it "osticket". Go back to osTicket on your browser and enter the database information. 
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/7c651124-343e-4b84-ba72-517794bc4f3d" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Success! Now let's clean up.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/3d368376-976d-4edf-98c4-696db04583f6" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Go back to "wwwroot" --> "inetpub" and right-click on "setup" and delete it.
</p>

<p>
<img src="https://github.com/delainee64/osticket-prereqs/assets/114307952/3a91b889-167b-4b61-be5e-6e0a2b517397" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Lastly, go to "Include" in the same file and right-click on "ost-config.php" and select properties --> "Security" --> "Advanced" and uncheck everything but "Read and execute" and "Read". Hit Apply and you are finished with setup!
</p>
