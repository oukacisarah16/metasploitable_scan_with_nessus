# Metasploitable_scan_with_nessus
## Step 1: Metasploitable machine
**1-** Download metasploitable vulnerable Linux virtual machine(we call it VM1).<br />
**2-** Choose Nat network<br />
**3-** enter with username msfadmin password msf admin<br />
**4-** type ifconfig to see his inet addr(I obtain 10.0.2.4)<br />
**5-** In another Linux Virtual machine(we call it VM2) open terminal, than I type `ping 10.0.2.4` to see if we can access to it<br />
<br />
## Step 2: Nessus scanner
**1-** Download nessus in VM2.<br />
**2-** open terminal(VM2), than I type `dpkg -i nessusfile` for setting up.<br />
**3-** type `service nessusd status` to see if nessus is active.<br />
**4-** than type `netstat -tnlp` to see the port number of localhost (I obtain 0  :::8834).<br />
**5-** Go to browser than type `https://localhost:8834` .<br />
**6-** follow steps to open nessus essentials in browser .<br />
<br />
## Step 3: Scanning metasploitable using nessus
**1-** Run VM1 and VM2 in the same time.<br />
**2-** ensure that the two VMs have Nat Network in Adapter.<br />
**3-** ensure that VM1 is accessible by VM2 and that nessus essential is opened in VM2 {the two previous steps are successfully done}.<br />
**4-** In Vm2 I go to nessus in browser than I click new scan.<br />
**5-** I choose advanced scan .<br />
**6-** follow steps to create new scan ensuring that target is 10.0.2.4 .<br />
**7-** I add some sttings checked to do the scan properly .<br />
**8-** I launch the scan than I go to vulnerabilities to see the vulnirabilities detected .<br />
**9-** it shows me : (9 critical) (2 high) (41 medium) (9 low) (159 mixed).<br />
<br />
## Vulnerabilities Detected
I will note just the critical and high ones<br />
### Critical
**1-** SSL(multiple issues)                      *family:* Gain a shell remotely *Count:* 3<br />
**2-** Bind Shell Backdoor Detection             *family:* Backdoors <br /> 
**3-** NFS Exported Share Information Disclosure *family:* RPC<br />
**4-** rexecd Service Detection                  *family:* Service detection<br />
**5-** Unix Operating System Usupported Version Detection *family:* General<br />
**6-** UnrealIRCd Backdoor Detection             *family:* Backdoors <br />
**7-** VNC Server ''password'' Password          *family:* Gain a shell remotely<br />

### High
**1-** rlogin Service detection                  *family:* Service detection<br />
**2-** rsh Service Detection                     *family:* Service detection <br /> 


