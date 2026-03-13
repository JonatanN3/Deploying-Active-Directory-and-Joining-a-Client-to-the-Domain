<p align="center">
<img width="600" height="335" alt="image" src="https://github.com/user-attachments/assets/f5a3d652-196e-4dcf-814f-113a9cbb6f54" />



<h1>Deploying Active Directory and Joining a Client to the Domain</h1>
This tutorial focuses on establishing the necessary infrastructure in Microsoft Azure for an Active Directory deployment. This includes creating the required cloud resources, configuring a virtual network, deploying virtual machines, and confirming proper network communication between systems before implementing Active Directory Domain Services.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Azure Virtual Network
- Azure Resource Groups
- Remote Desktop Protocol (RDP)
- DNS

<h2>Operating Systems Used </h2>

- Windows Server 2022 (Datacenter Azure Edition Hotpatch-x64 Gen2)
- Windows 11 Pro (Version 25H2-x64)
  

<h2>Confirm Installation Selections</h2>

<img width="1536" height="1024" alt="LabA1" src="https://github.com/user-attachments/assets/46116115-7809-4cd5-87a7-7ffcb761e8ef" />
</p>
<p>
Steps:

Opened Server Manager on dc-1.
Clicked Manage in the top-right corner.
Selected Add Roles and Features.
Continued through the wizard until reaching Server Roles.
Selected Active Directory Domain Services.
Accepted the additional required features when prompted.
Continued through the wizard until reaching Confirm installation selections.
Reviewed the selected roles and features, including:
Active Directory Domain Services
Group Policy Management
Remote Server Administration Tools
Checked Restart the destination server automatically if required.
Clicked Install.

Explanation
This step confirms that the server is about to install the components required for Active Directory. Installing the AD DS role is the first step toward turning the Windows Server machine into a functioning Domain Controller.

<h2>Configuration Required After Installation</h2>

<img width="1536" height="1024" alt="LabA3" src="https://github.com/user-attachments/assets/4e909d5c-7227-4891-b8a2-8e9d66107b3a" />
</p>
<p>
Steps:
  
Waited for the installation to finish.
Reviewed the completion message in the wizard.
Confirmed that the message stated:
installation succeeded
additional steps are required
Located the link:
 Promote this server to a domain controller
Prepared to begin the post-deployment configuration process.

Explanation
Installing the AD DS role does not automatically create a domain. At this point, the role is installed, but the server still needs to be promoted to a Domain Controller before it can manage users, computers, and authentication.
.

<h2>Start the Domain Controller Promotion Process</h2>

<img width="1536" height="1024" alt="LabA4" src="https://github.com/user-attachments/assets/88381e84-c40f-4951-833f-54f5edb9e987" />

</p>
<p>
Step:

Returned to Server Manager.
Clicked the notification flag in the upper-right corner.
Reviewed the post-deployment message for Active Directory Domain Services.
Clicked Promote this server to a domain controller.
Waited for the Active Directory Domain Services Configuration Wizard to open.

Explanation
This step begins the actual domain setup process. In a real IT environment, this is where the server transitions from being a basic Windows Server installation to becoming a Domain Controller.


<h2>Configure Domain Controller Options/h2>
  
<img width="1536" height="1024" alt="LabA6" src="https://github.com/user-attachments/assets/013176d7-3c87-47a7-b32e-62fa0d78b196" />

</p>
<p>
Steps:
  
-Continued through the configuration wizard after selecting deployment settings.
Reached the Domain Controller Options page.
Set the Forest functional level.
Set the Domain functional level.
Left DNS Server checked.
Left Global Catalog (GC) checked.
Left Read Only Domain Controller (RODC) unchecked.
Entered the Directory Services Restore Mode (DSRM) password.
Confirmed the DSRM password.
Clicked Next.

Explanation
These settings define how the Domain Controller will function in the environment. DNS is required because Active Directory depends heavily on name resolution, and the DSRM password is used for recovery and troubleshooting tasks if Active Directory needs to be restored.


<h2> Run the Prerequisites Check</h2>

<p>
<img width="1536" height="1024" alt="LabA9" src="https://github.com/user-attachments/assets/8b38698d-d6a9-4047-92af-379970b043e9" />
</p>
<p>
Step:
  

Continued through the remaining configuration pages.
Reached Prerequisites Check.
Waited while Windows validated the configuration.
Reviewed any warnings or informational notes.
Confirmed that the checks passed successfully.
Clicked Install to begin the Domain Controller promotion.

Explanation
This validation step is important because it confirms that the server is properly configured for promotion. In a production environment, this helps prevent configuration problems before Active Directory is installed.


<h2>Domain Controller Promotion Completed</h2>

<p>
<img width="1536" height="1024" alt="LabA21" src="https://github.com/user-attachments/assets/6f7cc0cb-cf7e-4a65-94f3-800f1bbc68c1" />
</p>
<p>
Steps:
  
Waited for the installation and promotion process to complete.
Reviewed the final result message.
Confirmed that the message stated:
 This server was successfully configured as a domain controller
Reviewed any final notes shown by the wizard.
Prepared for the automatic sign-out and restart.

Explanation
This step confirms that Active Directory has been successfully deployed. At this point, the server is no longer just a Windows Server VM — it is now a working Domain Controller capable of managing the domain.


<h2>Verify Server Manager After Restart</h2>

<p>
<img width="1536" height="1024" alt="LabA24" src="https://github.com/user-attachments/assets/c5d67c88-96e7-4b02-ad9b-924d88d4f93f" />
</p>
<p>
Steps:
  
Logged back into dc-1 after the restart.
Opened Server Manager.
Reviewed the dashboard.
Confirmed that AD DS and DNS were now installed server roles.
Verified that the server was ready for Active Directory administration.

Explanation
This step confirms that the reboot completed successfully and that the new Domain Controller roles are active. DNS and AD DS are both essential for managing a Windows domain environment.

<h2>Verify the Domain in Active Directory Users and Computers/h2>

<p>
<img width="1536" height="1024" alt="LabA26" src="https://github.com/user-attachments/assets/32aeaa00-4f23-4ac9-8cb9-262cef558387" />

</p>
<p>
Steps:

Opened Server Manager.
Clicked Tools.
Selected Active Directory Users and Computers.
Waited for the management console to open.
Expanded the left-side pane.
Located the newly created domain.
Expanded the domain to view the default containers, such as:
Users
Computers
Domain Controllers

Explanation
This confirms that the domain was created successfully and that the Active Directory structure is now available for administration. This is one of the first places an IT administrator checks after promoting a Domain Controller.


<h2> Create the _EMPLOYEES Organizational Unit</h2>

<img width="1536" height="1024" alt="LabA28" src="https://github.com/user-attachments/assets/ea90c386-6d5f-4d06-b9cc-578965a8a223" />
</p>
<p>
Step:
  
In Active Directory Users and Computers, right-clicked the domain name.
Selected New.
Clicked Organizational Unit.
Entered the name:
 _EMPLOYEES
Left Protect container from accidental deletion checked.
Clicked OK.

Explanation
Organizational Units are used to organize users and computers inside Active Directory. This makes administration easier and allows policies to be applied to specific groups of objects. Creating OUs is a common best practice in IT environments.


<h2>Join Client-1 to the Domain</h2>

<p>
<img width="1536" height="1024" alt="LabA31" src="https://github.com/user-attachments/assets/035951ca-779a-4108-8b15-5cf32d8f3e8d" />
</p>
<p>
Step:
  
Logged into Client-1.
Opened Settings.
Navigated to System > About.
Selected the option to rename the PC or join a domain/workgroup.
Opened the Computer Name/Domain Changes window.
Selected Domain.
Entered the domain name:
 mydomain.com
Clicked OK.
Entered domain administrator credentials when prompted.
Accepted the domain join.
Confirmed the successful domain join message.

Explanation
Joining the client machine to the domain allows it to be managed through Active Directory. In a business environment, this is how workstations become part of the company network and can use centralized authentication and policy settings.


<h2>Verify Client-1 Appears in Active Directory</h2>

<img width="1536" height="1024" alt="LabA35" src="https://github.com/user-attachments/assets/46f34c9e-d331-4756-87db-7bfbec444b41" />
</p>
<p>
Step:
  
Returned to Active Directory Users and Computers on the Domain Controller.
Expanded the domain structure.
Clicked the Computers container.
Looked for Client-1 in the object list.
Confirmed that its object type was Computer.
Verified that the client had successfully joined the domain.

Explanation
This final verification step confirms that the client machine is now part of the Active Directory environment. From an IT support perspective, this is an important check because it proves the domain join worked correctly and the client can now be managed through the domain.


<h2>Summary</h2>
  
By the end of this section, the Windows Server machine had been successfully promoted to a Domain Controller, the new domain had been verified in Active Directory, an Organizational Unit had been created for better organization, and the Windows client machine had been joined to the domain. These steps established the core Active Directory environment needed for user, computer, and policy management.

.


