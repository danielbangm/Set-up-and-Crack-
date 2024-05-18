<p align="center">
<img src="https://i.ytimg.com/vi/XjVYl1Ts6XI/maxresdefault.jpg" />
</p>

<h1>John the Ripper: Set Up and Crach Hash Password</h1>

In this exercise, I will download a zip file containing the “passwd” and “shadow” files from my Kali environment and utilize them to create a single password.txt file for John to crack. 

<h2>Objectives</h2>

-  Learning John the Ripper essential commands.
-  Exploring vraious kali linux commands.
-  Learning more about John the Ripper. 

<h2>Environments and Technologies Used</h2>

- Virtual Machine
- Kali Linux VM
- VMWare Workstation
- John the Ripper

<h2>Operating Systems Used</h2>

- Linux

<h2>List of Prerequisites</h2>

- You need to download VMWare Workstation and have a computer of at least 8GB of RAM. Also download Kali Linux VM 

<h2>Projects steps</h2>

-  Step 1: Download The zip file 

I opened Firefox as user Kali and downloaded the zip file. File will download to <b>/home/kali/Downloads</b>. Now open a regular terminal and do "cd /home/kali/Downloads" , and then "ls -al" to double check the downloaded file is there.
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/d1b7c04a-5eb8-46e7-8474-fb1ece759789)

-  Step 2: Let's Unzip the file and validate

First and foremost let’s sudo as root so that we don’t have to worry about privledges. let's use the command <b>sudo su</b>
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/8028ce48-63fe-4ea5-9120-94a4d540c1e7)

Now let's unzip the file and validate by using the command <b>unzip john-files.zip</b> follow by <b>ls -al</b>
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/8d7498ec-b6bc-4f8b-a3eb-46e2f8c56628)

- Step 3: Create a Single file from the passwd and shadow files

Now, we will use the “unshadow” command, a tool that “John the Ripper” contains that allows us to create a single file from the passwd and shadow files. <b></b>unshadow passwd shadow > mypasswd.txt</b>. ls -al (Always validate. Is the mypasswd.txt file there?)
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/8cf314e3-15c0-470f-8dcf-92181a20d680)

- Step 4: Decrypt the file

Now that we have the file to be potentially decrypted, we are going to use a specific word list for the decrypt.  Open another “root” window. cd /usr/share/wordlists, gunzip rockyou.txt.gz, ls -al ( you should see the rockyou.txt file)
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/42dd2c83-40ca-4604-a606-911e094092b8)

- Step 5: Continuing Decryption with John the Ripper

Go back to the other window, location: /home/Kali/Downloads Now, Let’s try to descript. Enter the following command: <b>john –wordlist=/usr/share/wordlists/rockyou.txt –format-crypt /home/kali/Downloads/mypasswd.txt</b> This may take a while. It depends on the CPU and Memory of the System. We told it to use the word list rockyou.txt and use the “crypt” format, which is the encryption that our Linux is using for the password encryption.
![image](https://github.com/danielbangm/Set-up-and-Crack-/assets/22795502/fb313613-d72f-4032-8ae2-95598ba3f173)

At this point, “John the Ripper” will start trying to unencrypt the password file. This can take some time. Days as an example. For the purposes of this lab, just let it go for an hour or if you want to have fun, then let it run overnight







