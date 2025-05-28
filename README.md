# HTB-Campfire-2


<h2>Description</h2>
Hack The Box Sherlock (Campfire-2) – Investigating AsREP Roasting with Splunk

Forela’s network detected suspicious activity: an alert flagged an old, inactive admin account requesting a ticket from the KDC on a domain controller. Since the account had pre-authentication disabled, an AsREP Roasting attack was suspected. Using Splunk, event logs were ingested and parsed to trace Kerberos authentication attempts. SPL queries were used to filter for EventCode=4768 and accounts without pre-auth, revealing the targeted user and the attack vector. This enabled rapid identification of the adversary's footprint and supported lateral movement analysis, ultimately leading to root access and full machine compromise.

<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Splunk</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)


<h2>Program walk-through:</h2>
<br/>
<br/>

<p align="center">
<h3>Task 1: When did the ASREP Roasting attack occur, and when did the attacker request the Kerberos ticket for the vulnerable user?
<br/>
</h1> </br>
<br />
<img src="https://i.imgur.com/l2eAMZy.png"/>
<br />
<img src="https://i.imgur.com/Hf8m1JB.png"/>
<br />
<br />
<h3>Task 2: Please confirm the User Account that was targeted by the attacker.</h3>  <br/>
</h1><br/>
<br />
<img src="https://i.imgur.com/jNCUwk9.png"/>
<br />
<br />
<h3>Task 3:What was the SID of the account?</h3> <br/>
</h1><br/>
<br />
<img src="https://i.imgur.com/Zu5Vwyj.png"/>
<br />
<br />
<h3>Task 4: It is crucial to identify the compromised user account and the workstation responsible for this attack. Please list the internal IP address of the compromised asset to assist our threat-hunting team. <br/>
</h1> <br/>
<br />
<img src="https://i.imgur.com/A8OtAKP.png"/>
<br />
<br />
<img src="https://i.imgur.com/z0VDwf5.png"/>
<br />
<br />
<h3>Task 5: We do not have any artifacts from the source machine yet. Using the same DC Security logs, can you confirm the user account used to perform the ASREP Roasting attack so we can contain the compromised account/s? <br/>
</h3> <br/>
<br />
<br />

<br />
<br /> 
<h3> Thanks for going through my documentation! Please let me know of any improvements.  </h3>
<h1/> 
<br />
<br />
