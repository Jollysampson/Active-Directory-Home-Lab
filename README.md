# Building An Active Directory Home Lab
---
<img width="630" height="301" alt="Image" src="https://github.com/user-attachments/assets/d5383313-72c0-4b2e-b3d7-6fc49c8099c0" />

---

# Introduction

**Active Directory (AD) is the backbone of user and access management in most Windows enterprise networks. This project demonstrates how to build a simple Active Directory home lab from scratch for hands-on learning and practice.**

# What is Active Directory?

**Active Directory is Microsoft’s centralized system for managing users, computers, and permissions within a Windows domain. It handles authentication and access control, making it essential in enterprise environments.**

# What is a Domain Controller?
**A Domain Controller (DC) is the central and most critical component in an Active Directory environment. It stores the directory (our phonebook) and handles authentication, authorization, and administrative tasks such as managing user accounts, applying group policies and enforcing security settings. Essentially, it is the brain behind the AD environment.**

# Why this Project?
If you’ve ever wanted to build your own Active Directory lab but weren’t sure where to begin, you’re in the right place. In this article, I’ll guide you step-by-step through setting up an AD lab environment that’s perfect for learning, testing, or practicing cybersecurity skills.



Disclaimer:
This guide is intended strictly for educational and ethical purposes. All configurations and demonstrations should only be performed in a controlled, isolated lab environment that you own or have explicit permission to use. Do not attempt to replicate any part of this setup on production systems or unauthorized networks. I am not liable for any misuse of the information provided.



---

Lab Requirements
Set up the following virtual machines using VMware Workstation:

- 1 x Windows Server 2022 (Domain controller)
- 2 x Windows 10 Enterprise — User-machine 1 and 2
- 
  - Minimum System Requirements:

RAM — Minimum 16GB
Disk Space — Minimum 60GB  
---
***Downloading Required ISOs***
Download the required ISOs from the official Microsoft Evaluation Center using the links below:**

Windows 10 ISO
Windows Server 2022 ISO
<img width="1400" height="543" alt="Image" src="https://github.com/user-attachments/assets/81fdd69b-5d5f-4c2e-b026-06f02be3871a" />

<img width="720" height="315" alt="Image" src="https://github.com/user-attachments/assets/c3157602-fa7d-4a7b-8ab4-32bf64393724" />

Simply complete the trial registration form to access the download. You don’t need to use a real name or email. Just fill it out and click Download.

<img width="720" height="322" alt="Image" src="https://github.com/user-attachments/assets/67855426-26bc-4f31-b50c-400cfbecd536" />

<img width="1400" height="682" alt="Image" src="https://github.com/user-attachments/assets/020ba4d1-93c6-46a3-81d7-85f18867d266" />

Ensure you download the 64-bit edition.

<img width="1400" height="671" alt="Image" src="https://github.com/user-attachments/assets/362c0351-59d2-463e-821a-beebe94b8d51" />

<img width="1400" height="641" alt="Image" src="https://github.com/user-attachments/assets/e841c4e8-92b1-401f-90b3-fde8b87d4b94" />

---

# Setting up the Domain Controller

Once you’ve downloaded the required files, we’ll move on to configuring  **Windows Server 2022** in VMware to set up the **domain controller.**

Start by creating a new virtual machine, then select the ISO file.

<img width="1400" height="516" alt="Image" src="https://github.com/user-attachments/assets/d53951d9-2a32-4b71-8e35-e22336b805f0" />

<img width="640" height="634" alt="Image" src="https://github.com/user-attachments/assets/ff5e1f15-fb8c-48e5-8b83-b2088763e0eb" />

Select the Windows Server 2022 **ISO file**, then click **Next.**
<img width="636" height="636" alt="Image" src="https://github.com/user-attachments/assets/c36e96d0-8391-4061-8f2a-6af41911f469" />

Select the operating system and version. The highest server version in the list is Windows Server 2016, which is fine.


<img width="640" height="631" alt="Image" src="https://github.com/user-attachments/assets/9172d8bc-4b10-480f-916f-ed9634ede3a3" />

Choose a storage location for the virtual machine, then click Next.
![1_0mZRE4JJi9w3XSRxdgq3dA](https://github.com/user-attachments/assets/212a4b8a-3f6a-4772-9467-24390ab665ce)

Make sure to select a drive with at least **60 GB of free space** to store your files.
![1_UGG7Tmdl9kpW21oWcP2_Qg](https://github.com/user-attachments/assets/11b6de7c-d66d-4f2c-b104-e055cd89b210)

![1_WSoqz7LL0ig3UFWR3jEkvA](https://github.com/user-attachments/assets/68256bd0-883b-41c9-a4bd-ad80618af35e)

Before powering on the machine, let’s adjust the virtual machine settings.
![1_QvJHfSUzrf8MnSozOeNmGg](https://github.com/user-attachments/assets/c9dcdb6d-a9dc-4a06-ab62-4e27d281d666)


Allocate sufficient memory based on your system’s capacity. For this demonstration, I’m using 4 GB of RAM. Also, ensure the network setting is configured to NAT.

![1_Qci_y-340sJ7nvRWxHen4w](https://github.com/user-attachments/assets/8a1f5265-4447-4fd1-a98d-5cf9ec19566a)

Now power on virtual machine and quickly press any key to begin the installation.
![1_3l1zVF3YXxQ0NHEY5pBiBQ](https://github.com/user-attachments/assets/c0eb1ed7-81a1-4cc0-8060-b6fca3e8d17d)


Follow the on-screen prompts to complete the installation.

![1_vV1tXVSd_QT1WEQjyQ9_QA](https://github.com/user-attachments/assets/3854f7d4-5f64-4a04-bd4c-54154f55a03d)
![1_Erz5UsemLaieIAfGr2ukvw](https://github.com/user-attachments/assets/3cd444dc-2b14-4553-be40-2896684392d4)



Select Windows Server 2022 Standard Evaluation (Desktop Experience) from the list.
![1_rLRE1PTi7ejAOdlea5-NPA](https://github.com/user-attachments/assets/7b65bbe1-607c-4a0d-aa01-7b0858cb41bd)
![1_3gn9zoSorBXSKYwhxeR2hQ](https://github.com/user-attachments/assets/41324a40-073b-4b40-b5ce-d4a8eb88edac)


Click on Custom: Install.

![1_H51NbNlr-QEh8tFuuLSK9w](https://github.com/user-attachments/assets/252b76fa-c740-453b-91f4-1ce7b7c7dfdf)

Create a new drive by clicking New, then apply the changes to proceed.
![1_8eDuqC3ROWh09HfGgg4Zrw](https://github.com/user-attachments/assets/047c0df1-65df-4827-ab90-e36cdedf0dba)
![1_4dog5Ax3Lh_X6l4PJd42Kg](https://github.com/user-attachments/assets/40ea5005-3ce6-445d-bb48-532181cce25f)
![1__9u1ywfJYtrjcRsX6nfVSQ](https://github.com/user-attachments/assets/8243c120-b393-4689-b498-9357503ce11b)


The installation may take some time, so be patient.
![1__91pLMBzS4I3Ydgxh5Srsw](https://github.com/user-attachments/assets/754b6f5a-aaea-4ef3-9388-71c6029c53ad)


Allow the machine to reboot automatically. This may take a few minutes to complete the installation.
![1_QUe95how9KzzrChtRsed_g](https://github.com/user-attachments/assets/200610f9-f45e-4e4f-8545-0482676a01d4)


You’ll now be prompted to create a password for the Administrator account. For this demonstration, I’m using a weak password.
![1_fi1bXPyZ4WNtFBJulXK9Wg](https://github.com/user-attachments/assets/5e4562ba-0d3a-419a-8995-bdb35a936ea5)


Use the Send Ctrl + Alt + Del option to unlock the screen.
![1_4cOK2yCmIkSzMmFryWAwkQ](https://github.com/user-attachments/assets/41233195-f580-4d72-89a4-f1e9ac5e4b4a)


Enter the password to log in.
![1_TGI3slhFhUXlo8shgDXoKg](https://github.com/user-attachments/assets/59ada65f-7f61-4c74-9df9-4a642f976a7b)


Once logged in, the first step is to rename the computer.
![1_nLQ-higRzgcN2lglDU1kUA](https://github.com/user-attachments/assets/6fa516e4-5c14-4246-a068-1887841c2939)


Click on Rename this PC and enter your preferred name, such as HYDRA-DC.

![1_nhFbZOxJoIJit0CgOl77og](https://github.com/user-attachments/assets/19bb66f0-9ced-4761-8b10-64131b9f58d7)
![1_T2HfPYoFXDIYT-GnOqCcEw](https://github.com/user-attachments/assets/3c262158-454b-4ccd-8790-cc5c85fc4dbd)


Proceed to restart the machine.
![1_wHtlECaRykpg_CpadTr3rA](https://github.com/user-attachments/assets/c7e063aa-6d9d-46d4-9143-d08a98c2a586)


Log back in. Now, to set up this system as a domain controller, start by adding Roles and Features. Click Next until you reach the Server Roles step.
![1_SQjqlvBfJkdxLcSALsCGaw](https://github.com/user-attachments/assets/914dfa5b-aff7-42f8-90e8-b33d3d882670)


Check Active Directory Domain Services and click Add Features. Then continue clicking Next to proceed.
![1_YXP1DBXis2CXB5D6cBt5BA](https://github.com/user-attachments/assets/e2784600-6da6-49c9-b351-0a23336a7764)


Check the option Restart the destination server automatically if required, then click Install.
![1_YXP1DBXis2CXB5D6cBt5BA](https://github.com/user-attachments/assets/60bd3726-782d-4f78-a08b-d753e1b2169a)
![1_oKQzBKRhJqLuDk3zfiUHSg](https://github.com/user-attachments/assets/34514833-b921-4804-82fe-658af7b27ec6)




The installation will take a few minutes to complete and set up the domain controller.
![1_nT8YYmISyaroWcQLuE3bHw](https://github.com/user-attachments/assets/5eb59b16-2016-49c5-ac63-875119791e62)


After the installation completes, proceed to promote the server to a domain controller.
![1_banJxdeWpUaUprKa2LUz6A](https://github.com/user-attachments/assets/9b466fdc-fc84-4fd6-9823-b6a5ee0de44b)


Create a new forest and enter a domain name of your choice. Once done, click Next.
![1_xWkUaba8ZUPoecjz4TIltg](https://github.com/user-attachments/assets/85920589-5340-4ed4-95e0-328114dfcf1d)


Set and confirm a password for Directory Services Restore Mode, then continue clicking Next until you reach the Prerequisites Check section.
![1_SGtkWXK9TnpSihx5uHMg0A](https://github.com/user-attachments/assets/e216b32f-97fb-4ee7-bbba-c6305af001ca)


Wait for the prerequisite check to complete, then click Install to proceed.
![1_6OEJSJLml4lTzsSwcbwYKg](https://github.com/user-attachments/assets/8f158a22-999b-41ce-b2aa-0867b24d4ed0)
![1_aKwAydusVKmLdnuObJVgfw](https://github.com/user-attachments/assets/638e74fa-a703-4574-9dd9-2aeecec74ced)


The installation will begin and prompt a reboot once finished. Click Close and the system will restart automatically and return to the login screen.
![1_HD-36puazu633CCDyvwtdg](https://github.com/user-attachments/assets/e08622fe-25f1-4392-8d60-502f31abd6f5)
![1_lnq37tk7ZOut1hUyaDrjlg](https://github.com/user-attachments/assets/e45eb642-ad5b-44bc-a40a-5ead0bceb853)


We can now see that the login is being performed as MARVEL\Administrator.
![1_sNkGTvudtnrIWNYMq9Qfgg](https://github.com/user-attachments/assets/5b46dac2-55c2-44c5-9524-1c488dd9e32b)

Next, we need to set up Active Directory Certificate Services (AD CS), which will allow us to perform certain attacks later. Open Add Roles and Features again and click Next to continue.
![1_gmr1kV8XsspC_4hM-xDnJg](https://github.com/user-attachments/assets/eaa35fc0-41d6-4da1-8dc0-d7b3f15601e7)

Select Active Directory Certificate Services. In simple terms, Certificate Services are used to validate identities within a domain environment.
![1_rSt99kibjkK3s5j4Uv980w](https://github.com/user-attachments/assets/0e5e6108-5fac-4a45-8128-2a71867beeba)

Keep clicking Next to proceed through the setup.
![1_kMe_NpvbfEsW9xGFPYhmYA](https://github.com/user-attachments/assets/ad1795f1-9cc3-4783-919f-8b7f59d2f6be)
![1_Dmpbj7gUAWiT6kKyLqf1VQ](https://github.com/user-attachments/assets/22f2ab74-23b6-4281-aef2-edb907c6bb2f)


Ensure that Certification Authority is selected before continuing.
![1_yBJnsNBg7wFMrHVas4hcjw](https://github.com/user-attachments/assets/483af5a7-54ab-4e93-a591-af334fa11623)

Select Restart destination server automatically if required, then click Install to begin the setup.
![1_6NGOegleIa9g3tJ66zqgwg](https://github.com/user-attachments/assets/efb99038-680e-4609-b0fd-e2671415b808)

Once the installation is complete, proceed to configure AD CS on the destination server.
![1_w1Bym_6YGqt4tIVeB74ZwQ](https://github.com/user-attachments/assets/404fe580-c48d-4aa2-94cf-3812c9e51629)
![1_e3gB4F6X9_Rxj_OlkmPEIQ](https://github.com/user-attachments/assets/882c2ccd-7c5f-440c-b0f9-a3819bcccd89)


**Ensure that Certification Authority is checked, then continue clicking Next to move through the configuration steps.**

![1_otsKJqrhdZ-TBelw1FgZWA](https://github.com/user-attachments/assets/92e894f7-40e1-4ca9-8739-4ddb033597aa)

On the Cryptography settings page, leaving SHA256 as the default is perfectly fine.
![1_ppe3U_6zX77wqcEZOejuJA](https://github.com/user-attachments/assets/a6f0e12c-f7ff-41c1-baf4-0543aa3f0bb5)
![1_vcQ6F9xEoh0ujSn2CP9SsQ](https://github.com/user-attachments/assets/77ae363f-f574-4319-a699-bc6865047f1c)


**For the validity period, set it to 99 years in case you plan to keep this lab environment running long term.**
![1_sK5hZ3XBXyRTKcPDtLMJdQ](https://github.com/user-attachments/assets/d9f54fe9-c96e-4186-ba60-0677984f908e)
![1_Lr0iyoobxiXg5TUbbCFA_Q](https://github.com/user-attachments/assets/5e5798ef-936b-41b3-8eb3-2aa0289f8405)


**That’s it for this section. Go ahead and reboot your server so we can move on to setting up the user machines.**
![1_9DUWeLLtVtpvgQ5lcomxoQ](https://github.com/user-attachments/assets/ca339f52-c1ce-4af0-ac8e-5db93a2fea90)
![1_XRRMP3CyIW3L2wH5XxDPmQ](https://github.com/user-attachments/assets/e999b81a-f260-4a3e-99c7-7ed21e16872f)


**Setting up the User Machines
Now that the domain controller is set up, it’s time to move on to the user machines. To conserve RAM, go ahead and shut down the domain controller for now.**
**We’ll be building two user machines in this next step.**
![1_C5harl5vdVCmF1iVVHuPyg](https://github.com/user-attachments/assets/2031f543-133c-4335-bf3e-32abd12e52ab)
![1_kDBnrcn2ly-VjELq5JvQ5g](https://github.com/user-attachments/assets/04944411-41ff-4a92-873b-0c69b24fb827)



**Go ahead and select the Windows ISO, then click Next to continue.**
![1_lGlfxafywjxhccw0yZFXQQ](https://github.com/user-attachments/assets/f901bccd-eebc-402c-a11c-496a40c327ea)


**Skip the product key step, and make sure to select Windows 10 Enterprise as the version.**
![1_Ck__ajKX6cofyna7GuxiRw](https://github.com/user-attachments/assets/c9769404-dcb6-459d-91e2-8660983a424c)
![1_8o7sqZAOhgOm0VmZvB5ehw](https://github.com/user-attachments/assets/36ea8eef-44ee-4e39-8dea-de7c37b10e4a)


**Give your virtual machine a name, feel free to use any name you prefer.**
![1_hESGfTV5kv1mWFcJUY8kYQ](https://github.com/user-attachments/assets/326c83d6-a70c-4e39-9d04-92fb9f5863fb)
![1_9o3dmFyos70cqXPP6Q-O-w](https://github.com/user-attachments/assets/cbb8d703-a7bd-4eb9-8002-091914c3a9e8)
![1_tpKHTZlEiIWelo5GXqCxwA](https://github.com/user-attachments/assets/7dd29f46-9f94-4249-91f4-58cddc3c3703)



**Next, we’ll edit the virtual machine settings and remove the floppy disk from the hardware configuration.**
![1_vuBvrbBYQoIk9OC03X57Zg](https://github.com/user-attachments/assets/87b57c56-9f65-4357-ae2e-dc2cd4e65480)
![1_YnjDZnvMZ4E3iynTwmA-lQ](https://github.com/user-attachments/assets/e782dbe7-c208-49e1-a67a-485b337977c7)
![1_h_Il1KuCDEeoLwFnhFTh9g](https://github.com/user-attachments/assets/1022fe66-b2f1-4d64-9662-69c0![1_jYY5EAgRXm7O76v4z2HlQg](https://github.com/user-attachments/assets/34f3e1c4-e8af-4141-8d25-a6be4914a95b)
a59fca39)


**You can leave the memory at 2GB, and make sure the Network Adapter is set to NAT. Once that’s done, go ahead and power on the machine.**
![1_h_Il1KuCDEeoLwFnhFTh9g](https://github.com/user-attachments/assets/7cb76c15-52f4-460c-baba-074c19c8025b)
![1_jYY5EAgRXm7O76v4z2HlQg](https://github.com/user-attachments/assets/de649510-30f6-4eac-928d-41b2ff71ced4)
![1_zRTf0ePTI_xAzK8HjNdbBQ](https://github.com/user-attachments/assets/9e3000ae-98c2-4a75-87ad-1b9081b8e21d)


**Follow the installation prompts just like you did for Windows Server 2022. This part should be quicker, as it’s mostly a repetition of earlier steps. Let the machine reboot automatically when prompted.**
![1_4zSfOBeKKdx2GrGkC4yCMQ](https://github.com/user-attachments/assets/5cb3f11d-8852-44d3-b92d-82e3b3ab3399)
![1_Y7-trzm_if8hj4VfViOQlA](https://github.com/user-attachments/assets/c0dd6603-1179-460a-8e5b-7793f0f1c838)


**When prompted, go ahead and skip the keyboard layout selection.**
![1_HTW_4QsijiCvcJIeN4BVyw](https://github.com/user-attachments/assets/e96d7acd-e77d-4552-afbf-2d6beffde654)

**At this point, you’ll see a screen asking if you want to sign in with a Microsoft account. Select Domain join instead.**
![1_iZDtwntuBGXe1T5wNV3yxA](https://github.com/user-attachments/assets/5b77a2aa-d147-4741-9909-93208f27ef47)


**This option allows you to create a local account instead of signing in with a Microsoft account. Feel free to use any name of your choice for the username.**
![1_K5twCkhduwu97EiALm_kPg](https://github.com/user-attachments/assets/35ed8f59-66b4-4178-a955-3e9cc719909b)


**Set a password and confirm it. For this lab, I’m using a weak password just to keep things simple.
Password1**
![1_QWtmUqkmL_C-1wFr7bK0Mg](https://github.com/user-attachments/assets/0c6c67a2-3d9f-40ab-a928-6d076743df1b)

**For the security questions, feel free to select any options and provide answers of your choice.**
![1_uh-Z0gYMfmwoc5oPTpUwTQ](https://github.com/user-attachments/assets/8a8be2cf-5c76-4952-97fd-cf0513c06e67)



**Next, we’ll disable location services and turn off other optional settings to minimize data sharing.**
![1_k7u8h2BroQPrOwF_kMNf0g](https://github.com/user-attachments/assets/c68d13b4-6fd7-4b89-91ae-2e7761532ef8)
![1_fjVRVYNE8yRMOs8UUHL1QA](https://github.com/user-attachments/assets/7da4d48e-e040-4ee5-9676-d7f9dc337975)


**Great, now that you’re logged in, go ahead and rename the PC to something meaningful for your lab setup.**
![1_4o9x5pjpx73snZAmusjOJA](https://github.com/user-attachments/assets/b528225c-5f85-4338-86ab-0e28a11c6fb8)
![1_gxwpCS1bshjeeP0LZBs7QQ](https://github.com/user-attachments/assets/84b6b1b5-c120-4d85-b143-2147c6a84d8d)


**Go ahead and restart the machine, then repeat the same setup process for the second user machine.**
![1_hRvvk2-eYJyz3EuapJGHuQ](https://github.com/user-attachments/assets/dcaf9755-c8c0-40e4-ac5f-6ec1e7488920)

# Second User Machine

*Machine Name: SPIDERMAN
username:     peterparker
password:     Password1*


# Setting up Users, Groups and Policies
**Next, we’ll modify the domain controller by setting up user groups and applying some policies. But first, let’s go ahead and power on the domain controller.**
![1_TBBbbb2HcxsPKMF5xjGRMg](https://github.com/user-attachments/assets/2856ceb7-2b25-48a6-8779-b6921b129bfc)
![1_jparPFT1sYVMV7v2hRlbPQ](https://github.com/user-attachments/assets/35740aea-8a45-4eb6-9809-c103f6921fd4)

**Right-click the domain name and select the option to create a new Organizational Unit (OU).**
![1_EzzII4Z3tppfezUCze0hYQ](https://github.com/user-attachments/assets/5616fe6f-39d4-49eb-8108-411cd38c4b4e)

**Give the Organizational Unit a name of your choice, then click OK to create it.**
![1_PospwuZNhfqw7YNEpCX_dg](https://github.com/user-attachments/assets/281c05af-c6cd-4192-9cbf-7684d2e8d3c3)
![1_Pbbil3exOh-0ysEGJONiRw](https://github.com/user-attachments/assets/00afe99f-bbf4-4b3f-8054-dfc94b361a73)


**Select all the users in the Users folder, excluding the Administrator and Guest accounts — then drag and drop them into the Groups folder (the Organizational Unit we just created).**
![1_VMMGt3F8ujg57liY8Aldlw](https://github.com/user-attachments/assets/0ac147de-9f2b-49a1-a4dd-42356f731899)
![1_vF8eY-CvNnKfFplvYVA20Q](https://github.com/user-attachments/assets/0d3f2fc7-4db3-4309-94de-bd8ff4cf4dc4)


**Now let’s create a few more accounts. First, we’ll create a Domain Admin account by duplicating the existing Administrator’s privileges. Right-click on the Administrator account, select  copy, and follow the prompts to set up the new account.**
![1_ZO_wilo0BAQtKreBDmYPjg](https://github.com/user-attachments/assets/846018ff-5336-4106-8eb6-08eae5a13264)
![1_DDWdcqO-B8kPNkimJsc87A](https://github.com/user-attachments/assets/183c3046-ecd3-44bb-8d04-917b7f633b5d)


**Set a password of your choice and make sure it’s something you’ll remember, then hit Next. I’m using a weak password here to keep things simple.**
# Password12345!
![1_3Q8BtJ9ZVpiptNGQfuwQjw](https://github.com/user-attachments/assets/83ea2102-e249-46dc-bd25-2c9b6e656187)
![1_ZCALI7wZvFcI8EYfN80Sqg](https://github.com/user-attachments/assets/2964b38b-e2d3-4563-bf23-96fac64ce931)


**The domain admin has now been successfully added.**
![1_tdqEHGMpNpARaRK2u9-1Ig](https://github.com/user-attachments/assets/ce33deec-b027-416b-891c-27c4667c8907)


**Next, let’s duplicate the Administrator account again to create a service account with domain admin privileges. Service accounts are typically used to run specific services, so in this case, we’ll create a SQL service account to manage a SQL Server instance.**
![1_reCf-WUuEy-xxKFroJ1yIA](https://github.com/user-attachments/assets/eb537579-0bcb-4621-a3f5-080cb5f5e7e5)

**Once again, set a password you’ll remember.**
# MYpassword123#
![1__sjMMjc8jr1rKyQbo-9XTQ](https://github.com/user-attachments/assets/ca834086-b21d-4dad-b88c-58e4a9b7431f)

**We can now see that the service account has been successfully created.**
![1_ezAKi1w851iQu-r9uovxrA](https://github.com/user-attachments/assets/7091829b-5104-4257-8bda-6f6be5c23582)

**Now double-click on it and add a note in the description field. We’re simulating what many domain admins do — assuming they’re the only ones who can see the password. In reality, any valid user can view the description.**
*The password is MYpassword123#*

**At this stage, let’s go ahead and create two standard users who will be part of the Domain Users group. To begin, right-click on an empty space in the user pane.**
![1_-onZiWlRTLLWcF4tqVXZ5g](https://github.com/user-attachments/assets/2ef73962-05a7-4e89-9b3c-50f9afcfa927)

**Now, follow the prompts to complete the creation of both user accounts.**

**First User
Frank Castle
fcastle
Password1**

**Second User
Peter Parker
pparker
Password2**

**All our accounts are now set up just the way we want them.**
![1_yo5pn1Jt3LfcLVZgSbcZKQ](https://github.com/user-attachments/assets/491b863a-e654-4ab0-a265-cce4b494cfb0)

**Let’s go ahead and create a file share that could potentially be exploited in future attack simulations.**
![1_rVyhUHVHXrd3Od3xxQtCAw](https://github.com/user-attachments/assets/f6833293-31de-4d14-9843-c91e35e69d6b)

Click on Shares in the left-hand pane to begin setting up a new shared folder.
![1_rUwGS3CYetWiGddlrj3Kag](https://github.com/user-attachments/assets/18b65988-cd81-4101-afeb-29b3cb7099f8)
![1_-XpqVJjRiXgi9LtrIse6dQ](https://github.com/user-attachments/assets/0588817a-45f7-4422-a687-adbd9183f918)


Keep clicking Next to proceed through the setup wizard.
![1_n_kgeV22vtEtXmX_6D_WvQ](https://github.com/user-attachments/assets/412298d9-15a0-4e1f-afdd-3fc28852512d)

Go ahead and enter a name for the share, this will be the name users see when accessing the shared folder.
![1_fittlfdmcEpQdYXQiDO7ag](https://github.com/user-attachments/assets/f9ea5afc-ef08-4d2c-b96e-6132674ce9dd)
![1_qZnRmJtBINdN4VLoEr9yvQ](https://github.com/user-attachments/assets/b47445be-2876-4d6c-b2af-57b976c308ac)


Keep clicking Next through the remaining prompts, then click Create to finish setting up the file share.
![1_wCQnXyJliM8JHrQ5sKCSfQ](https://github.com/user-attachments/assets/dd39ab3c-bdcc-41da-a8d2-1df78ced05f3)
![1_Aj-4PZm8hWi_ef8jDZTBnQ](https://github.com/user-attachments/assets/0f07277c-21e2-42d3-9f6b-860c7dc4ac5f)


Next, we’re going to complete the SQL Service setup using the command prompt with administrative privileges.
![1_EvPf3ODuliKiKmJhBrAjTA](https://github.com/user-attachments/assets/da684ae6-e531-4ab3-bbe3-a7831ca5d937)

Run the below command, making sure to replace it with the actual name of your domain controller.
# setspn -a HYDRA-DC/SQLService.MARVEL.local:60111 MARVEL\SQLService
![1_rOtZ19PbLSPV217x8JMFpw](https://github.com/user-attachments/assets/68c348a5-4be5-4791-bb7c-84cf0f589ad8)

Confirm that the Service Principal Name (SPN) was successfully found.
# setspn -T MARVEL.local -Q */*
![1_GkR0Lf4OmU5w1wkFHSFTPQ](https://github.com/user-attachments/assets/a74b5a5a-55bb-47ce-993d-786af5e9acab)

Now we’re going to set up a Group Policy.
![1_FraIb5hw3dKbx9k1SVXj2Q](https://github.com/user-attachments/assets/1ea885ba-dbfe-4a24-9cfb-5eee3482d2ab)

Next, let’s add a new policy. We’ll be creating a Group Policy that applies across the entire domain.
![1_M8r7umDjRM48ekIYBsENQw](https://github.com/user-attachments/assets/171fe3ae-2e7e-434f-b582-aa471f1b1df1)

Go ahead and give the policy a descriptive name so it’s easy to identify later.
![1_J3upzv7Qx9bSaZarxvypeA](https://github.com/user-attachments/assets/6dbe8541-5b3e-43f1-b42f-a434d3101c35)

Now, let’s edit the newly created policy by right-clicking on it and selecting Edit.
![1_N469b9_bR1JHk1PoPxjEfw](https://github.com/user-attachments/assets/c1954a77-a28d-4c51-a248-91f79699f094)
![1_SR2oaEEe7xySQ2UluFEnaA](https://github.com/user-attachments/assets/a61d4eec-5f6d-4c51-96ec-6d9e3a7dac1c)


Now we’re going to disable Windows Defender in our lab environment. This will allow us to execute various attack techniques freely. Please note that this lab setup does not cover antivirus evasion techniques.
![1_jlTdjmpRlMtjpxhT2QJH4w](https://github.com/user-attachments/assets/38ef701e-9b1c-4da3-9001-d8507277729e)

Scroll down to find Microsoft Defender Antivirus, then double-click it and set it to Enabled to turn it off.
![1_5zA5c3BGjPqAM_3KoeDcrA](https://github.com/user-attachments/assets/a1ed7138-b13e-477c-93c9-6ddeacb69ea9)
![1_bT4WX8DSlxxHM3WtbfRkQg](https://github.com/user-attachments/assets/82fa6a54-a04c-4fb5-b81d-a45562a4a6c8)


Now we need to enforce the policy we just created. This ensures that any user or machine that joins the domain will automatically have Windows Defender disabled in accordance with the policy.
![1_KGam4LV8z1uKajn2LsS6dQ](https://github.com/user-attachments/assets/fca10f7c-43bf-4ce6-b33f-b9628dce296d)
![1_HRBJqa4aYGbzYvNP1v8d9Q](https://github.com/user-attachments/assets/f26e9560-b51f-42e8-9c6c-e3158ce8bfb0)


The final step is to configure a static IP address for the domain controller. Start by opening command prompt and checking the current IP configuration of the machine.
![1__rzFl4Oeiq_CgXzh_WT2bw](https://github.com/user-attachments/assets/31e6c3a1-0476-4b0a-af2c-dad18780fc87)

Next, click on Network & Internet Settings from the taskbar.
![1_kbZgQc1UK75FOoafkxGp6A](https://github.com/user-attachments/assets/6ff7cf68-3e28-4453-a3e9-d102487a9b8e)
![1_Nx4DDUqMME3aEr5GiG_vBA](https://github.com/user-attachments/assets/df294b80-e700-4a8f-9efb-cb28cc69f7be)
![1_xSkK-Y5ceHkod1CxxBop9g](https://github.com/user-attachments/assets/3eeee800-97fd-4e00-97c9-c671079b5dcd)



Double-click on IPv4 and update the IP address, subnet mask, and default gateway based on your preferred network configuration. You can choose any values that suit your setup.
![1_xFxV5W6ZC-0Bm_pZyq_Z4Q](https://github.com/user-attachments/assets/79c76e4c-941c-43bb-9872-3adf1a4d742d)
![1_lnNr-6hAmviIb_uNY2oslA](https://github.com/user-attachments/assets/b5cb8e9d-9d0f-42d9-979e-3a8421fd3908)

---

Next, we’ll proceed to join the user machines to our domain controller.

Joining our Machines to the Domain Controller
At this stage, we’re going to join both user machines to the domain controller. Ensure all machines are powered on before proceeding.

Become a member
First, we need to configure the DNS settings on both user machines by pointing them to the domain controller’s IP address. Make sure to apply this change on both systems.
![1_Xx1zpc1887U_6AmAp9Q_1A](https://github.com/user-attachments/assets/e3b8b12e-5400-4476-8fb5-54794b0a9cce)


Next, we’ll connect the machines to the domain. Search for Domain in the Start menu and select Access work or school from the results.
![1_g70s-HPaex_nTikgT3BV7w](https://github.com/user-attachments/assets/293a3e37-b669-46d3-8cf2-d632ece466e2)
![1_SlHCm036yWVLqm5Vg8TH9A](https://github.com/user-attachments/assets/a448e21a-d203-4dd6-b349-8175aaee42fd)
![1_n5n1B_Z4VnRV0GXcrHBX2g](https://github.com/user-attachments/assets/3da57cea-f3a2-40a9-96f5-956c91c0f7e7)



Type in the domain name and click Next.
![1_yTfPWkJmsg1n6ZUjmWlvog](https://github.com/user-attachments/assets/8111841b-243c-47aa-8726-57257a878be3)

Now sign in using the Administrator credentials and click OK.
![1_yoDFier7GEq7fq1V9MUKHA](https://github.com/user-attachments/assets/7232638b-e318-49f1-9cc7-065737dcb8a4)
![1_znbTcqSjnAxF1gJqcpxsZg](https://github.com/user-attachments/assets/e7da405b-6742-4357-970a-78a19329f2f0)



Next, go to the second machine and repeat the same steps. Once done, log back into the domain controller to verify that both machines have successfully joined the domain.
![1_3d52Gy5s3bLPkqEmZuJqPw](https://github.com/user-attachments/assets/0fbc2e70-6e14-4d5e-a182-4ccb83f4019c)

Under the Computers section, we can now see that both machines have been successfully added to the domain.
![1_zh3pDSW5zuCqhno5dKJDqA](https://github.com/user-attachments/assets/3961d5fd-f855-47b0-8f9f-9f71cc70fad7)

Now let’s switch back to the THEPUNISHER machine and log in as the administrator — we’ve got a few quick configurations to take care of.
![1_kCXGZtdIto3BDxSkDjpwPg](https://github.com/user-attachments/assets/193acf31-af24-4b16-8aef-1da003d44083)

Click on Manage Local Users and Groups.
![1_Rxqih2nqvhY58CNfm1gL7A](https://github.com/user-attachments/assets/a9e5ba0a-a38a-49dd-b5ff-8b3ee3326607)

Under Users, set a password for the local Administrator account.
![1_Z5xWjS8dJ-xunga5tXxYMQ](https://github.com/user-attachments/assets/2b5d2915-7a57-4c8d-a33b-bfd3cd94f35d)

I added this password.
Password1!
![1_ekIxg5WDODjcgMuMqXrdww](https://github.com/user-attachments/assets/5d9b00ea-457d-4411-b4c3-8baf0488538a)

Now, double-click on the Administrator account, uncheck Account is disabled, and click OK.
![1_j8lbaccSCqLO1fQu46tIfw](https://github.com/user-attachments/assets/1fe6856e-f8d1-4858-bd4b-ceaa06d5ad51)

The account is now enabled. While best practice recommends keeping it disabled, in many real-world environments you’ll often find local Administrator accounts left enabled. In the Groups section, we need to add one more user, Fcastle to the Administrators group.
![1_1NFjwaKyBQdDkwtxErbYbw](https://github.com/user-attachments/assets/65a6798f-8382-4b2e-b5f5-6daf0d794464)
![1_pUgG6Fcu2zIdILI2PkDQRg](https://github.com/user-attachments/assets/f4b66677-f196-4e84-b8e3-2a5139fa3d69)


Type in the username, click Check Names to validate it, then click OK to confirm.
![1_2P3YVPl65d_rN2Bjg6MLPg](https://github.com/user-attachments/assets/0c53bbaf-9fe1-480c-b4f6-a9b5d3ba880f)


Now let’s ensure that Network Discovery is enabled on this machine.
![1_vjurgR6ddW4Y-U6xaLvwEQ](https://github.com/user-attachments/assets/321bb31a-2172-43e9-91ff-438290d3e2d3)

Click on Network, and you’ll notice that Network Discovery is currently turned off.
![1_x6gpMhRyOATfGu_P567d5Q](https://github.com/user-attachments/assets/92e732ed-c1dc-4513-a722-5b0f9b7ae10d)
![1_hXk0MnvJXmX0i8aDzFQi1w](https://github.com/user-attachments/assets/a2570f2f-5228-45cf-8071-4626e2920f36)


Network Discovery is now successfully turned on.
![1_UPWgElDBGekaENeqqvToIg](https://github.com/user-attachments/assets/02e133cf-51c3-41ea-bf3d-628b0d1f9610)

Now move on to the second machine and repeat the same steps. This time, we’ll be adding two users pparker and fcastle to the local administrators group.
![1_BAUr4f-7bggDCuo6dgzseg](https://github.com/user-attachments/assets/98122b5b-0099-48f4-8b10-3a11c9c0137e)

Also, make sure to turn on Network Discovery. Once that’s done, sign out of the SPIDERMAN machine and log back in as the local Administrator.
![1_1m6yPJCNk2io09wQfCZR-Q](https://github.com/user-attachments/assets/434ccc6e-b21a-40b2-a987-0c86a55a6272)

Next, we’re going to set up a shared drive.
![1_m8rI0zZZwEHOiG3zCRfikw](https://github.com/user-attachments/assets/3120498a-6da9-47f0-95bd-3f7cf0c67a18)

Click on This PC, then select Map network drive from the top menu.
![1_eWSvaS9oiQp7md6Uh39Hlw](https://github.com/user-attachments/assets/e49759dc-3505-4bd2-90db-f574e75b4e6f)
![1_3Hqjit9OLQvIpHuvd7KI7w](https://github.com/user-attachments/assets/504456c3-099c-4c9e-9e8a-9416df2a8c7d)


Enter the Administrator credentials when prompted to authenticate the connection.
![1_BUh3b9icIlcqdd8itQjiwA](https://github.com/user-attachments/assets/be8e5fef-ffe2-4f1d-966c-9a421b0d43bb)

Now the shared drive has been successfully mapped and is accessible from this machine.
![1_iADqw8P3H5Gu4b8YR0Aswg](https://github.com/user-attachments/assets/3ebe626f-c686-40d7-b08a-f6f7982505bb)

**Conclusion**

**This project demonstrates how to build and manage an Active Directory home lab from scratch. Through this setup, I gained hands-on experience with domain controllers, user and group management, Group Policy configuration, and joining client machines to a domain.**

**Building this lab helped strengthen practical IT Help Desk skills and improved my understanding of real-world Active Directory environments. Continuous practice with labs like this is essential for supporting users and maintaining reliable Windows-based networks.**




