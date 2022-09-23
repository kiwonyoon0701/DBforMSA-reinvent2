## Event Engine Region - ap-northeast-2 (Seoul)

---



# Create Key pair

1. Login to the AWS Management Console.

---

2. Service => Search window => Move to the EC2

![image-1](/static/image-1.png)

---

3. In the left pane, "Network & Security" => "Key Pairs" Click

![image-2](/static/image-2.png)

---

4. Click the "Create ky pair" button

![image-3](/static/image-3.png)

---

5. Name : `DBforMSA` and click the "Create key pair" button

![image-4](/static/image-4.png)

---

6. You can see DBforMSA.cer or DBforMSA.pem file on your computer downloaded.

   This file should be managed securely.

![image-5](/static/image-5.png)

---

7. You can see the key file in the management console.

![image-6](/static/image-6.png)



---

---

# Environment Configuration

1. Move to the CloudFormation console.

![image-7](/static/image-7.png)

---

2. "Stack" => "Create stack" => "With new resources(standard)"  Click

![image-8](/static/image-8.png)

---

3. Enter `https://shared-kiwony.s3.ap-northeast-2.amazonaws.com/OnPREM4.yml` and click "Next"

![image-9](/static/image-9.png)

---

4. Stack name : `DBforMSA`   
   KeyName : `DBforMSA`

![image-10](/static/image-10.png)

---

5. "Configure stack options" - Click "Next"

6. In the "Review DBforMSA" page, check `I acknowledge that AWS CloudFormation might create IAM resources with custom names.` and click "Create stack"

![image-11](/static/image-11.png)

---

7. You can see the progress on the "Events" tab.(It will complete in about 10 minutes.)

![image-12](/static/image-12.png)



**`CREATE_COMPLTE`**

![image-13](/static/image-13.png)

---

---

# Connect to the bastion host server

---

1. CloudFormation => Outputs => `IPWindowsPublicIP`

![image-14](/static/image-14.png)

---

2. Connect to the bastion host using "RDP Client"( Windows : mstsc.exe, MAC : Microsoft Remote Desktop)

**Windows Laptop**

![image-20220207104404321](/static/image-20220207104404321.png)

![image-20220207105101422](/static/image-20220207105101422.png)



**MAC Laptop**

![image-20220207105204837](/static/image-20220207105204837.png)

---

3. Connect to the bastion 

   ```
   User : Administrator
   Password : Octank#1234
   ```

   

![image-20220207105237250](/static/image-20220207105237250.png)



![image-20220207105240390](/static/image-20220207105240390.png)

---

4. Copy `DBforMSA.cer(or DBforMSA.pem)` file downloaded to the bastion server.

**If your pc is a MAC laptop**

![image-20220308160910914](/static/image-20220308160910914.png)



**If your pc is a Windows laptop**

![image-20220308161206849](/static/image-20220308161206849.png)



**Paste the pem file into C:\keys in the Bastion Server.**



![image-20220308161721721](/static/image-20220308161721721.png)

![image-20220308161802763](/static/image-20220308161802763.png)

---

5. Execute MobaXterm(SSH Terminal Program).

![image-20220308161915397](/static/image-20220308161915397.png)



---

6. Choose "OracleServer" =>  "Edit session"

![image-20220207140508645](/static/image-20220207140508645.png)

---

7. Configure the pem key to connec to Oracle server
   1. "Advanced SSH Sessting"
   2. Check "Use private Key"
   3. Click "Open Key"
   4. Move to the "C:\keys"
   5. Chooose the "DBforMSA.cer" and open
   6. "OK" Click

![image-20220308165918129](/static/image-20220308165918129.png)



![image-20220308170039842](/static/image-20220308170039842.png)

---

8. Connect to the Oracle Server

   **Execute**

![image-20220207141433762](/static/image-20220207141433762.png)

**Click Accept**

![image-20220207141628256](/static/image-20220207141628256.png)



**You connected the Oracle server**

![image-20220207141741293](/static/image-20220207141741293.png)



---

[To the next - workshop01(Separation of CRM Report Service Using MongoDB) ](../workshop01/index.en.md) 
