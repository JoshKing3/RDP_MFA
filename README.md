![image](https://github.com/user-attachments/assets/7699e4b0-1f26-44f1-a3bf-97b91e82c103)


# Implementing Duo Multi-Factor Authentication (MFA) for Azure Server 2019 RDP Access

## Introduction
A password represents something you know, and your phone represents something you have — combining them enables secure access with Duo.

In this lab, I will demonstrate how we can enhance the security of our Azure Server 2019 VM by implementing Multi-Factor Authentication (MFA) with Duo for RDP access.

This focuses on securing an Azure environment by implementing an additional layer of authentication, guaranteeing that only authorized users can gain access.

### Cisco Duo Documentation
- [Cisco Duo RDP Documentation](https://duo.com/docs/rdp#first-steps)
  
![image](https://github.com/user-attachments/assets/d6fee898-c07a-422c-9bf7-0e0f1c539665)


---


## Step 1: Create Azure VM
1. Select the **Windows Server 2019 Datacenter — x64 Gen2** Image.
   
   ![image](https://github.com/user-attachments/assets/d0d72f71-fb9e-454d-93cd-cd76ef786563)

3. Create a User Account:
   - Ensure **Remote Desktop Protocol (RDP)** on **Port 3389** is selected.
     
     ![image](https://github.com/user-attachments/assets/94b3d0be-6cc9-46b9-84c8-c47ce2fbb116)

  
---

## Step 2: Sign Up for Duo & Create a User
1. Register for a free trial on Duo: [Duo Free Trial](https://signup.duo.com/)
   
   ![image](https://github.com/user-attachments/assets/0c64a416-e2c9-4cf4-acb3-194d00d6a265)

3. Navigate to the **Users** section on the left-hand side, and click on **Add User**.
   
   ![image](https://github.com/user-attachments/assets/99a41582-d661-4ae4-8e5b-0a776e3dc9ef)

5. Fill out the fields, and an email confirmation will be sent for access.

   ![image](https://github.com/user-attachments/assets/0fb88ad8-7d30-404d-acb5-7e8188c86e9d)

   - Click **Send Enrollment Email** in the top right-hand corner.

     ![image](https://github.com/user-attachments/assets/da996ed5-1743-4247-93c4-c1e7be3c3651)

7. Open the email, launch the Duo mobile app on your phone, and scan the QR code.

 ![image](https://github.com/user-attachments/assets/6b1a57ba-9f09-4a3d-8412-2c7bb3cc9754)



---

## Step 3: Install Duo Authentication for Windows on Azure VM
1. RDP into the **Server 2019 VM**.

   ![image](https://github.com/user-attachments/assets/7804c01f-fd24-4ba2-ac5f-7aa7694f0d89)

3. Open a browser in your VM and log into the Duo Admin interface: [Duo Admin Login](https://admin.duosecurity.com/login?next=%2F)

   ![image](https://github.com/user-attachments/assets/9c5c69e5-45c3-434c-a0f0-d26271c77ff2)

5. Under **Applications**, click on **Protect an Application**.
6. Search for **RDP** and click on **Protect**:

   ![image](https://github.com/user-attachments/assets/a4093eaa-008e-41f4-818a-01e19446e002)

8. Using the Documentation page, download the **Duo Authentication for Windows Logon installer package**.
   - Found in the **First Steps** section under "Contents."
9. Open the downloaded file.

    ![image](https://github.com/user-attachments/assets/8d8e9f1f-abd1-4b51-8afb-db0d7ae4cf87)

11. Copy and paste the **API Hostname**, the **Integration Key**, and the **Secret Key** into the installer.

    ![image](https://github.com/user-attachments/assets/3b1f7790-59da-46f8-85ba-2b5fdfc1d9bd)

    ![image](https://github.com/user-attachments/assets/e6334446-9e3d-423d-ad2e-f315fee1bc41)


13. Click **Next** until the installation is complete.
14. Restart your VM after finishing the installation.

---

## Step 4: Log In as a User to Test
1. Once Duo Security is installed, RDP into the **Server 2019 VM** as the user you created earlier.

   ![image](https://github.com/user-attachments/assets/34a06d59-6263-4659-8229-f109bcd8e7f4)

3. The VM will now require Multi-Factor Authentication (MFA) for every Remote Desktop Protocol (RDP) login.

---

## Conclusion
Duo Multi-Factor Authentication (MFA) strengthens Azure Server security by seamlessly integrating an additional layer of authentication.

In the event of a data breach, a username-password combination can be easily compromised. However, this additional authentication factor keeps your data secure, as accessing an account requires something uniquely tied to you.
