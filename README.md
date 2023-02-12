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

Go to https://portal.azure.com You should already have your FREE subscription setup already. Click on Resource Groups and select "create" to make a new  group. You can name your resouce group "RG-osTicket". Select the region of your choice and click "Review + create" at the bottom left of the screen. After it finishes validating you can press create.  
<p>
<img src="https://i.imgur.com/WmQdVlm.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
</p>
<br />


Next we will go to the top search bar and type in "Virtual Machine", you should see the icon appear. Click create and choose "Azure virtual machine". Set your resource group to the same one you just created previously. You can name your Virtual Machine "VM-osTicket". Make sure you region you select atches the region for your resource group (THIS IS VERY CRITICAL IN ORDER FOR EVERYTHING TO RUN SMOOTHLY). Where you see "Image" select Windows 10 Pro (notice that your region will change automatically so make sure you set your region back to whatever you had it at previously to match the resource group). 
<p>
<img src="https://i.imgur.com/ejdJPAk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />


When selecting a size you want to select an option that can power 2 or more VCPU's. The more storage will help your VM run faster and prevent lagging when you remote desktop into your VM later. You also want to choose your own "USER NAME" AND "PASSWORD" (remember it for later).
<p>
<img src="https://i.imgur.com/9riUAit.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />


Press next until you get to 'Networking', you will notice that the VNet and SubNet will automatically generate for us. Click on 'Review + create' and your VM will validate. Next press create after it finishes validating.
<p>
<img src="https://i.imgur.com/R89OtVN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />
<img src="https://i.imgur.com/oUiurS9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
The VM will then create (give it some time). This concludes the first few steps in creating our VM environment. Next we will install osTicket and other resources. 
