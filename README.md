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
</h1> The screenshot below shows a result whenever you look up ASREP Roasting attack through google. We can see it mentions event code "4768" Kerberos authentication ticket was requested. Now with that information we can query event code "4768". Now to look for the right event we can look for the value "0x17" for the Ticket Encryption type, this indicates RC4 encryption is weaker associated with roasting attacks. </br>
<br />
<img src="https://i.imgur.com/2NpYDyX.png"/>
<br />
<img src="https://i.imgur.com/RKHX7uc.png"/>
<br />
<img src="https://i.imgur.com/DuDsD05.png"/>
<br />
<br />
<h3>Task 2: Please confirm the User Account that was targeted by the attacker.</h3>  <br/>
</h1>We go back to the same event and look for the account name section.<br/>
<br />
<img src="https://i.imgur.com/luTxJoX.png"/>
<br />
<br />
<h3>Task 3:What was the SID of the account?</h3> <br/>
</h1>Same thing we go back to the same event and look for the SID or service ID of the account.<br/>
<br />
<img src="https://i.imgur.com/YWthfMa.png"/>
<br />
<br />
<h3>Task 4: It is crucial to identify the compromised user account and the workstation responsible for this attack. Please list the internal IP address of the compromised asset to assist our threat-hunting team. <br/>
</h1>Now go to the Client address section and we should find the Internal IP address of the compromised asset. <br/>
<br />
<img src="https://i.imgur.com/sWs95qR.png"/>
<br />
<br />
<h3>Task 5: We do not have any artifacts from the source machine yet. Using the same DC Security logs, can you confirm the user account used to perform the ASREP Roasting attack so we can contain the compromised account/s? <br/>
</h1>This one is quite tricky since we do not have any artifacts. Now to start what I did and go to the left hand side panel and click on the account names, here I found an account name 
"happy.grunwald". Now we can type that as an answer and see if it works but that is just not good practice. We further investigate so we can be 100% sure if this is the account responsible. Next thing I did is to go back to the left hand panel and click on event codes, here I went one by one and see what each code meant. Then I came across event code "4769" which is the event code for Kerberos service ticket was requested. So now we query that event code and go through the events. Going through the events I found that the same account produced these event code. Which confirms out suspicion. Thus happy.grunwald being the user account who performed the ASREP Roasting Attack. <br/>
<br />
<br />
<img src="https://i.imgur.com/TbJKCeE.png"/>
<br />
<img src="https://i.imgur.com/FckmLO3.png"/>
<br />
<img src="https://i.imgur.com/FckmLO3.png"/>
<br /> 
<h3> Thanks for going through my documentation! Please let me know of any improvements.  </h3>
<h1/> 
<br />
<br />
