<h1>Audit Policies</h1>

<h2>Description</h2>
Project consists of using Group Policy to effectively monitor object access and logon events. This project is completed under the assumption that Windows Server 2016 is configured with a working domain environment and a Windows 10 client is added to that domain.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Group Policy Management</b>

<h2>Environments Used </h2>

- <b>Windows Server 2016</b>
- <b>Windows 10</b>

<h2>Configure an Audit Policy:</h2>
A new GPO named Audit Policy is created on the domain controller: <br/>
<img src="https://imagizer.imageshack.com/img923/5922/pw7vpV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The GPO is verified as created: <br/>
<img src="https://imagizer.imageshack.com/img922/2931/ZhYRCb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
GPO is edited: <br/>
<img src="https://imagizer.imageshack.com/img924/7857/YoHffN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Audit Policy is navigated to: <br/>
<img src="https://imagizer.imageshack.com/img922/2168/0c0Z2p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Audit object access is selected: <br/>
<img src="https://imagizer.imageshack.com/img922/2871/ZmWsFs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The policy is defined to include successful and failed logon attempts: <br/>
<img src="https://imagizer.imageshack.com/img924/5338/nQ5GWh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Audit policy is verified as changed: <br/>
<img src="https://imagizer.imageshack.com/img923/875/KRafEs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
GPO is linked to the Domain Controllers Organizational Unit: <br/>
<img src="https://imagizer.imageshack.com/img922/4442/jqTwjA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<h2>Create an Audited Directory:</h2>
A folder on the C: disk is created named Audited: <br/>
<img src="https://imagizer.imageshack.com/img923/2569/Qib6dC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Folder is shared with the Sales account (created in a previous project): <br/>
<img src="https://imagizer.imageshack.com/img922/6804/c8Ka2k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Share this folder is selected: <br/>
<img src="https://imagizer.imageshack.com/img924/9575/SjmH74.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Salesperson1 is added and granted Change/Read access: <br/>
<img src="https://imagizer.imageshack.com/img924/2862/f4WQ1I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Audited directory's properties is opened. Security tab selected, Advanced: <br/>
<img src="https://imagizer.imageshack.com/img924/3166/PDwZtu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Auditing tab is selected and Add is clicked. Select a principal is then selected: <br/>
<img src="https://imagizer.imageshack.com/img923/6984/S7tPc8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Domain Users is added to the principal: <br/>
<img src="https://imagizer.imageshack.com/img924/5055/zy94mp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Under the Type dropdown, All is selected. Write is checked: <br/>
<img src="https://imagizer.imageshack.com/img922/3853/1KG4AS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Apply, OK to close and verify: <br/>
<img src="https://imagizer.imageshack.com/img923/5482/slS7wI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Policy is updated via command gpupdate /force: <br/>
<img src="https://imagizer.imageshack.com/img924/707/ZAwRni.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Windows 10 client is opened and a text file is created within the shared directory: <br/>
<img src="https://imagizer.imageshack.com/img924/4891/siEi8l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the domain controller, Event Viewer is then opened to locate log 4663. : <br/>
<img src="https://imagizer.imageshack.com/img923/5729/XzeJgg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The audit is verified as collected: <br/>
<img src="https://imagizer.imageshack.com/img922/5572/4Ebh86.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<h2>Create an Audited Directory:</h2>
On the domain controller the GPO Audit Policy is edited Audit account logon events is selected. The policy is defined to audit successful and failed logon attempts: <br/>
<img src="https://imagizer.imageshack.com/img924/7523/VObd6V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The policy is updated per gpudate /force: <br/>
<img src="https://imagizer.imageshack.com/img923/9352/kRGzs8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Singing off the domain controller and attempting to sign back in using a failed password will show a log: <br/>
<img src="https://imagizer.imageshack.com/img923/5083/9nxvVZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The log that then recorded the successful sign-in is located: <br/>
<img src="https://imagizer.imageshack.com/img923/751/mvEVmk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
