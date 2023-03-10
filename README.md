# osticket-prereqs
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

- Azure Free Subscription
- Resource Group
- Virtual Machine
- Virtual Network (creates itself within VM)
- Subnet (creates itself within VM)

<h2>Installation Steps</h2>

1.1 Go to https://portal.azure.com You should already have your FREE subscription setup already. Click on Resource Groups and select "create" to make a new  group. You can name your resouce group "RG-osTicket". Select the region of your choice and click "Review + create" at the bottom left of the screen. After it finishes validating you can press create.  
<p>
<img src="https://i.imgur.com/WmQdVlm.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
</p>
<br />


1.2 Next we will go to the top search bar and type in "Virtual Machine", you should see the icon appear. Click create and choose "Azure virtual machine". Set your resource group to the same one you just created previously. You can name your Virtual Machine "VM-osTicket". Make sure you region you select atches the region for your resource group (THIS IS VERY CRITICAL IN ORDER FOR EVERYTHING TO RUN SMOOTHLY). Where you see "Image" select Windows 10 Pro (notice that your region will change automatically so make sure you set your region back to whatever you had it at previously to match the resource group). 
<p>
<img src="https://i.imgur.com/ejdJPAk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />


1.3 When selecting a size you want to select an option that can power 2 or more VCPU's. The more storage will help your VM run faster and prevent lagging when you remote desktop into your VM later. You also want to choose your own "USER NAME" AND "PASSWORD" (remember it for later).
<p>
<img src="https://i.imgur.com/9riUAit.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />


1.4 Press next until you get to 'Networking', you will notice that the VNet and SubNet will automatically generate for us. Click on 'Review + create' and your VM will validate. Next press create after it finishes validating.
<p>
<img src="https://i.imgur.com/R89OtVN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />
                                                                                                 
                                                                                                 
The VM will then create (give it some time). This concludes the first few steps in creating our VM environment. Next we will install Remote Desktop (if you do not have it already), osTicket and other resources.                                                                                                 
<img src="https://i.imgur.com/oUiurS9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
                                                                                                 
</p>
<br />
                                                                                                 
                                                                                                 
2.0 Next we will open up the VM-osTicket machine we created and copy the IP Address. We will use that IP address to remote desktop into our VM enviornment. (If you are using a Windows machine then just go to the start menu and type in "Remote" and it should appear. For MAC users like myself we will have to download "Microsoft Remote Desktop" from the app store first). Open your remote desktop and paste the IP address and you will need to use your User_name & Password that you created when we made the VM to open it.                                                                                                
<img src="https://i.imgur.com/YP5eGnU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                
                                                                                                 

2.1 Once you are logged in you will see "Choose privacy settings", just set everything to 'No'. and accept. We will be installing 'IIS' with CGI (internet information services is a webserver that will allow the computer to serv up a website for us to open osTicket. CGI is the programming language that osTicket uses). Go to the start menu and open the control panel. Select programs and then select under program feature 'Turn windows features on or off'. Select ISS and expand it (+) and select world wide web and expand that and select CGI and press ok.

<img src="https://i.imgur.com/TVngRmZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />          

                                                                                                 
Open up microsoft edge and in your browser type in 127.0.0.1. This is a local loopback address and we will see if we can load a web page that runs off ourself. Press enter and your page should look exactly like this: 

<img src="https://i.imgur.com/uZJ4sW6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                    

                                                                                               
2.1 Next we will download and install PHPManager first and then Rewrite from the link provided. All download resources are in this link for when you need to install something for the remainder of the lab. Open up your 'Downloads folder' so that after you download something it's easier to access.                                                    https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 
<img src="https://i.imgur.com/ta245Ov.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />     

                                                                                                 
2.2 Go to the C:drive and create a new folder called 'PHP' and then go to the download link and download 'PHP 7.3.8'. We will download that and then extract the files into our PHP folder we created. WHen you right click on the file press ectract all and the browse and go to C: drive and slect your PHP folder and press ok and extract. Next we will download the VC redistrubte file. This is our Microsoft Visual C++.

<img src="https://i.imgur.com/ohtutvf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                  

                                                                                                 
2.3 Next we want to download 'MySQL' and install it. When you get to "setup type" choose 'TYPICAL' and press next. When you get to the 'Instance Configuration' choose 'STANDARD' and hit next and next again. Now we need to create a username and password (maybe write these down somehwere to remeber for this lab, you can use 'Password1' or whatever you choose). MySQL is pretty much creating a database for osTicket to store users and tickets that we will create. 

<img src="https://i.imgur.com/IiIsohA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                              

                                                                                                 
2.4 Next we will open IIS as an Administrator and register PHP. Go to the start menu, type IIS (right click it and press 'Run as Administrator'). Click PHP Manager. You will see that it is not enabled. Click on 'Register new PHP version'. Next we will browse our C: drive and select PHP folder and select 'php-cgi'press ok. Now PHP is enabled. Look to the left and select VM-osTicket and that will take you to the home page. Look to the right side and press 'Restart'. 

<img src="https://i.imgur.com/TuonRKB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                 

                                                                                                 
2.5 Now we will download osTicket. Use the download link provided previously. Go to downloads and double click the osTicket file. Open a separate window and open the C:Drive and look for 'inetpub' double click it and double click 'wwwroot' and we will drag our 'upload' folder from osTicket and copy it into our wwwroot folder. Next rename the 'upload' folder to osTicket. Go back to IIS and hit restart. On the left of the home page hit the down arrow on sites and then again on default web site and click osTicket. Look to the right of page and select 'Browse *:80(http)' and it should open up a OsTicket window. You'll notice that some extensions are not enabled so we will enable them in IIS. 

<img src="https://i.imgur.com/sbqEHfz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />   
                                                                                                 
                                                                                                 
2.6 Go back to IIS and choose sites and osTicket. Double click on PHP Manager and click 'enable or disable extensions'. We are going to enable 'php_imap.dll', 'php_intl.dll', and 'php_opcache.dll'. Refresh the osTicket browser we opened previously and notice the changes that took place. Most of the red disabled are now green enabled except the last two (thats ok). Now we will rename the ost-config.php. Go to inetpub and then wwwroot and click on the 'include' folder. Scroll downa nd look for 'ost-sampleconfig.php' and rename it to 'ost-config.php'. Next we will assign permissions. Right click the file and go to properties, go to security and then advance and disable inhertince and remove all permissions. Then add permissions and select principal. In the box below type "everyone" and press ok. Click the 'Full Control' box and hit ok and apply. 
 
<img src="https://i.imgur.com/Pigraim.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                

                                                                                                 
2.7 Now we will continue setting up osTicket in our browser. Click continue at the bottom. Here we will setup our user information. You can put whatever info you choose. Remember to write down your username and password incase you need it later in the lab. 

<img src="https://i.imgur.com/ClZyqQk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                 

                                                                                                 
2.8 Here we will download and install HeidiSQL (database client) which will give us access to the MySQL database we installed earlier. Installation is pretty simple. Once Heidi opens you will select 'New' and there we will see username and password. The user is automatically going to be 'root' and the password is what you created before. Click ok and now you can see we have access to the database. Right click 'Unnamed" create new and clcik database. We will put 'osTicket' as the name and click ok. Now go back to osTicket in the browser, scroll data to Database settings and input the username:root and whatever password you created. For the MySQL Database: you will put osTicket. Click install and CONGRADULATIONS! 
Here is the link to download HeidiSQL: https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe                                                                                            
<img src="https://i.imgur.com/IGJfVd1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />
<img src="https://i.imgur.com/4P9JSIn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />                                                                                                 
                                                                                                 

2.9 To end this portion of the lab we will just do a little clean up. GO to the C: drive, inetpub, wwwroot and select the 'setup' folder and delete it. The scroll up and go to the 'Include' folder double click it. Scroll down to 'ost-config.php' right click and select properties so we can reset permissions to read-only. Security, advance, go to 'everyone' and edit. uncheck everything except read and write and press ok and apply. Now you can check and see if your log-in credentials work. Remeber your username and password. http://localhost/osTicket/scp/login.php

<img src="https://i.imgur.com/55vtl3B.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<img src="https://i.imgur.com/1PVCaFi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />
