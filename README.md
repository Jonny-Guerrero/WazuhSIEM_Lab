<h1>Wazuh SIEM Lab</h1>

<h2>Description</h2>
This project shows how to implement a SIEM/XDR solution to view telemetry data using Wazuh.
<br />

<h2>Languages and Utilities Used</h2>

- <b>Powershell</b> 
- <b>CMD</b>
- <b>Oracle VM VirtualBox</b>
- <b>Wazuh XDR</b>
- <b>Firefox</b>

<h2>Environments Used </h2>

- <b>Windows 11 Pro</b>
- <b>Ubuntu Desktop</b>

<h2>Lab walk-through:</h2>

<p align="left">
<h3>Wazuh Installation Setup (Ubuntu VM)</h3>
  
1.	Set up a VM running Ubuntu Desktop: https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview
2.	Boot into the Ubuntu VM and open a Terminal window. 
3.	Log in as sudo to run the following command to install Wazuh:
<pre>curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a</pre>
<img src="https://github.com/user-attachments/assets/3a6f9a66-31c8-4e56-9a4f-9469ce3c7042" alt="WazuhSIEM_Lab Steps"/> 
<br /><br />

4.	During the installation process, create a password. It will then complete the installation:
<pre>INFO: --- Summary --- INFO: You can access the web interface https:// User: admin Password: INFO: Installation finished.</pre>

5.	Once the installation is complete, open a web browser and go to your Ubuntu VM’s local IP address. It should bring up the Wazuh Dashboard login page.
<img src="https://github.com/user-attachments/assets/f1ee71a3-f80c-435f-aff1-96ae65a71f2e" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

6.	Once logged in, you should see the Wazuh Dashboard. Note: Yours will not show any active agents initially.
<img src="https://github.com/user-attachments/assets/995c8d46-82fc-4bba-b592-629b24dd59a9" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

7.  Select “Deploy a new agent” in the Agents summary tab or menu. Fill in the details based on the Windows or VM machine you’ll be using to gather telemetry data from. Copy the agent installation command at the bottom of the page.
<img src="https://github.com/user-attachments/assets/9fb3024a-607f-4f59-8a8a-b5c0da289f58" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

<h3>Wazuh Agent Installation (Windows Client or VM)</h3>

1.	Open Powershell as admin (it won’t work on CMD) and run the copied installation command to install the Wazuh Agent on the client machine.
<img src="https://github.com/user-attachments/assets/6e996d17-81d9-4e8c-b4fd-74aa28c9a717" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

2.	Once the installation is complete, check that the agent is running with the following command:
<pre>Get-Service -Name WazuhSvc</pre>

3.	Start the Wazuh Service with the command:
<pre>net start wazuh agent</pre>
<img src="https://github.com/user-attachments/assets/2d353569-70c3-42f8-9ac0-54ef1cf9c750" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

4.	To confirm the agent is running, go to the following file path: C:\Program Files (x86)\ossec-agent\win32ui and open the Wazuh agent.
<img src="https://github.com/user-attachments/assets/6f5ec052-b980-46ad-91ba-513d2d7e61d0" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

<h3>Wazuh Dashboard</h3>

1.	Back on the Ubuntu VM, reload the Wazuh dashboard or restart the VM to confirm if the Windows agent is now showing up.
2.  Click on the active agent under the Agents Management/Status tab to see the active agent.
<img src="https://github.com/user-attachments/assets/8b7a575c-abcc-45dc-a28c-15342ac529b2" alt="WazuhSIEM_Lab Steps"/>
<br /><br />

3.	To confirm the agent is active and detected, you can also run the following command from Terminal:
<pre>sudo /var/ossec/bin/agent_control –l</pre>


