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

- Create Virtual Machine in Microsoft Azure
- Install/Enable Internet Information Services (IIS) in Windows with CGI and download PHP Manager for IIS
- Download and Install Rewrite Module and Create directory for PHP to unzip files
- Download and Intsall VC file and MySQL
- Register PHP in IIS and reload to install osTicket v1.15.8
- Enable required extensions to continue installation of osTicket
- Install HeidiSQL to link MySQL database to osTicket

<h2>Installation Steps</h2>

1.) The first thing you are going to want to do is create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Note, you will want to create a virtual machine with atleast 2 vcpus and 16 gbs of memory.

2.) Once you have created your virtual machine you will want to conncet to it by using the public ip address the vm is setup with. You will connect using the remote desktop connection app.




  
<p>
  
![Screenshot (105)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/6dd21590-acb8-43cc-b3c2-38e905b1e887)



</p>


<p>
  
![Screenshot (106)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/d3b8caae-2574-4cef-a7cf-cd87cbc06959)


</p>
<p>
3.) Once you have connected to your virtual machine you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.
</p>
<br />

<p>
  
![Screenshot (112)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/28cfca17-7ff4-4b86-863e-cfc6995d1305)


![Screenshot (107)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/4f3adedd-771e-4500-b881-5350bb32dfd7)


</p>
<p>
4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features

- World Wide Web Services -> Application Development Features -> [X] CGI [X] Common HTTP Features
<br />

![Screenshot (108)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/f7e35772-bddd-499f-98ad-f06d651dfa17)


![Screenshot (113)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/7407b042-7a0f-4572-aa86-19d5ada18a99)


![Screenshot (114)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/ee8b87db-6495-4d78-9d00-1e398807439b)

NOTE Make sure all Common HTTP Features are checked

To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 It should look something like this.

![Screenshot (111)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/a3332150-e2f0-4fae-9ece-d9a51807eaf1)


5.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) Go through the install wizard and complete the install.

6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

7.) Create a folder in the C drive called PHP.

8.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP

9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.

10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->


Make the new root password: Password1

![Screenshot (115)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/4031d626-a49c-4c41-a600-0dd767319b8e)

Execute the process on the next page.

![Screenshot (116)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/9f80652d-637a-4047-8d23-ba33110ac4a1)

11.) Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator. The program should look like this.

![Screenshot (117)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/a4e63a4d-c2c1-4d7a-bfd8-6fca0e7ec883)

12.) We will now want to register PHP from within IIS. Click on PHP Manager

![Screenshot (117)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/0d409a2f-1aaa-4a61-b537-90b9f78a47e6)

Register new PHP version.

![Screenshot (118)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/e82d180f-a09e-4376-b619-d073ae0a2868)

You will want to provide a path to the php executable file (php-cgi.exe)). Go to C Drive -> PHP -> click on php-cgi file.

![Screenshot (119)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/be78376b-739b-4ebd-b79f-952d2b46f4e5)

Restart the IIS server.

![Screenshot (120)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/a373b421-3d62-4914-8bb4-cc244a249288)


13.) Install osTicket v1.15.8 -Download osTicket from the Installation Files Folder -Extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename "upload" to "osTicket"

Reload IIS again.

14.) On IIS go to sites -> Default -> osTicket -On the right, click “Browse *:80”

![Screenshot (121)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/2a854d45-7305-4de6-b5a5-58b017ab527c)

Some extensions are not enabled on the osTicket browser.

![Screenshot (122)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/e5b64482-dd1f-4e8b-8a49-1d9558f09883)

To enable the extensions: -Go back to IIS, sites -> Default -> osTicket -Double click PHP manager -Click "Enable or disable an extension"

![Screenshot (117)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/e6388a5e-ead4-4a72-9619-2cd2d3248184)

![Screenshot (123)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/e74a938d-6669-437f-ba86-1553ee661037)

We will want to enable three extensions from here.

1.) php_imap.dll

2.) php_intl.dll

3.) php_opcache.dll

![Screenshot (124)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/f9441ff9-4560-444e-955f-3f4f4a106eaa)

15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder. Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

We are going to rename the ost-sampleconfig.php to ost-config.php

Now that we have renamed the files, right click on the file and go to properties. From there click security, click on advance, and disable the inheritance. We will select Remove all inherited permissions from this object.

Now we will add new permissions.

Click Add

![Screenshot (125)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/433ccc47-f25d-4524-af13-a200e4a06ad0)

Select a principal

![Screenshot (126)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/284371fe-c5a9-4f4e-b83d-5296d7acbc4d)

Type "Everyone" in the box.

![Screenshot (127)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/e67180ef-869a-4ab8-8f8a-13cb1e34fd58)

Make sure Full Control and all the other boxes are checked.

![Screenshot (128)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/cb6a738d-9f61-4086-b98f-26a7f76af218)

Click Apply and Ok.

![Screenshot (129)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/8f5c9ffa-9851-4e27-b5e9-08bddd38b3fb)

Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page. Fill out the page as required except the Database Settings at the bottom of the page. We will get to that.

We will want to download and install HeidiSQL from the Installation Files.

![Screenshot (130)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/9f7b9f5f-a063-4f24-a903-635d7e6584ce)

When the program is open we will create a new session in it.


![Screenshot (131)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/238e61cf-5482-4fe4-b52c-57b3852d60c5)

We want to make sure the username is root and the password is Password1.

![Screenshot (132)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/8d4d64dd-d4f2-4aa9-8d02-5b819a89432b)


 Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.

We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.


![Screenshot (134)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/a183a4d5-6c34-4b38-83f7-2c2bd115b2a6)

The last step is to do some clean up. We will want to delete the setup folder in our system. -Delete: C:\inetpub\wwwroot\osTicket\setup Only delete the setup folder and nothing else.

We then will want to set the permissions back to "Read" only in the ost-config.php file.


![Screenshot (135)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/2daf205e-3b24-4890-af8a-049df2f8e027)

![Screenshot (136)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/d8b1837a-405a-4f46-9f91-efec5c7fcfa3)


The last step after that is to login to osTicket on the browser.

![Screenshot (137)](https://github.com/JoshuaMoorecc/osticket-prereqs/assets/154629831/0f274c54-2bd9-4be4-a44b-d9026097a484)

Congrats! We have now successfully installed and setup osTicket!!!
