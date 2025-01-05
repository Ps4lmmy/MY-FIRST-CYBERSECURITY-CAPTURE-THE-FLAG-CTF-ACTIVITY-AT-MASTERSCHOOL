# MY-FIRST-CYBERSECURITY-CAPTURE-THE-FLAG-CTF-ACTIVITY-AT-MASTERSCHOOL

The CTF challenge covers the following aspects:

1. User and File Management
- **Task Details:**
    - **User Creation:** Start by creating a new user in the Linux system. Remember to assign the user a password for subsequent login purposes.
    - **User Switch:** Once the new user has been created, switch your session to that user. This step will involve using command-line authentication.
    - **Folder and File Creation:** As the new user, create a new directory. Create a file and write a simple message inside this directory. Your message could be something like "Hello from [your username]!". Remember to save the file before proceeding.
    - **Switch Back to Original User:** After successfully writing the message, switch back to your original user session, which for this exercise, is 'ctf'.
1. File System Flags
2. Webpage Flags
3. Hidden Flags Challenge
4. Hash Cracking

## STEP 1:

Connecting to the target machine using Secure Shell (SSH) with the syntax `ssh user@targetip`.
<img src='(https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/d1dfd723-cf25-4da6-ba33-a93da7d506a1/Untitled.jpeg)'>

When i connected to the machine i was welcomed with the **First Flag {h4ck3r5_r_us}.**  

## STEP 2: User creation & User Switch

This stage encompasses different tasks and for each a different syntax.

 syntax `sudo adduser sam` & `su sam`

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/97c91c13-1324-4da3-841f-5854d7027c92/Untitled.png)

From the image above we were able to create the user “Sam” and also switched to the user.

### STEP 3: Folder creation

syntax `mkdir ctf_exercise` 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/1ca210bb-c088-4407-ae8c-ce8eca6bcea4/Untitled.png)

from the image in Step 2, we created the user SAM, but the user was still in the directory of the user CTF where i had no permission to create a file in. so i navigated to the home directory using `cd home` then listed the items in the home directory with `ls` and navigated into Sam directory with `cd sam` after which i used `mkdir ctf_exercise` this created a folder called ctf_exercise.

### STEP 4: File Creation

Syntax: `touch message.txt`, `nano message.txt` , `cat > message.txt`

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/e31bee35-7b00-4745-b858-12b03cd0a6ac/Untitled.png)

i used the command `touch message.txt` to create a file called “message.txt” after which i used the `nano message.txt` command to write/edit my message “Hello from Sam” into the created file. there is another method to this which is by using the `cat > message.txt`   command to create the file and also append the text into the file.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/bc21d1eb-a3cb-4ce5-9607-b820affae0af/Untitled.png)

This tasks made me understand the usage of nano and also how to use the cat command adequately.

### **STEP 5: Switch back to Original User**

**syntax:** `su ctf`

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/c68f89b9-9c41-49bc-acc2-a3ed60b7d05e/Untitled.png)

**STEP 6: File System Flags**

This is the second challenge in the exercise and we were told that there are four(4) file system flags and one of them is in a file called “find_flag.txt”. this is actually a good hint and prompted me to use the find command `find / -name "find_flag.txt" -type f 2>/dev/null`

let me break this command down; 

1. find: The command-line utility used for searching files and directories in a Unix-like operating system.
2. /: Specifies the starting point for the search. it is the root directory, which is the top-level directory in the file system.
3. -name "find_flag.txt": This option specifies the name of the file to search for. In this case, the file name is "find_flag.txt". 
4. -type f: This option restricts the search to only files. The argument "f" stands for file.
5. 2>/dev/null: This part of the command is used to redirect error messages to /dev/null, which essentially discards them. The number "2" refers to the standard error (stderr), and /dev/null is a special file that represents nothingness. By doing this, any error messages produced during the search (such as permission denied messages for directories the user doesn't have access to) will not be displayed on the terminal.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/5232b47e-96df-487a-9a5f-cfea97f6f210/Untitled.png)

the find command returned the file path to us so we would use the `cat` command to open the file.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/06a5a8ce-e432-44c5-872f-7bf2ec0d07ac/Untitled.png)

There it is our first file system flag is {F1nd_FL4g_Fun}. 

**Second File System Flag:**

i listed all folders and files in ctf directory using `ls -lah` and voila i found a hidden file  .f.txt then i used the command `cat.f.txt` , i found another flag {H1d3_1n_pl41n_s1gh7}

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/4dd7d956-dfee-4d97-a26d-84f57bc12c95/Untitled.png)

**Third File System Flag :** 

i navigated into another folder “flag” using `cd flag` then listed all items in the folder with `ls -lah`

i found an interesting file “story.txt”. i opened it with `cat story.txt` and there was an interesting story of how cybersecurity experts saved the day. whilst reading this, i found another flag {St0ry_FL4g}. ****

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/95c741c9-402d-4947-b322-5a51a0a66549/Untitled.png)

**Fourth File System Flag:**

this wasn’t as easy as i expected, thanks to one of my colleagues Tom, he was the one who guided me on locating the last file system flag. it was just a simple find command to show all hidden files in the flag directory using `find . -type f` . this brought two results. the first which we had viewed earlier and the second which hasnt been viewed.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/e73f428e-5c9d-4f1e-9768-cfa62528506b/Untitled.png)

i opened the second using  `cat ./6/m/a/s/t/e/r/s/c/h/o/o/l/f_l_a_g.txt`  and i found the last flag which was (Y0u_G0T_1t} shown in the image below.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/5221ebd4-3ca4-47ec-af9b-2fa72ae0fe9b/Untitled.png)

### STEP 7: Webpage Flags

i was tasked to find flags hidden within webpages. what i did first was to scan the Ip address with the nmap which is a very powerful network scanning tool used to discover hosts and services on computer networks. the command used was `nmap targetipaddress -sV -vv -T4`

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/ba9b4573-543f-484a-81fc-d240883f8334/Untitled.png)

I found an http port open, so i pasted the Ip address of my target machine on my web browser and it showed me my first Webpage flag {STUDENT_CTF_WEB}

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/d1a08720-9034-498d-8a04-c579118ee7e1/Untitled.png)

at this point i was stuck but Tom came through again and believe me i learnt a lot from his teachings and it was an eye opener for me. The second flag was hiding in plain sight and that leads us to the source page of the above webpage. and the flag found was **{Another_Web_Flag}**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/096385e8-f137-4cee-bbf5-2b63596aa2fd/Untitled.png)

in the quest for the third flag, Tom introduced me to a tool which shows hidden pages on a webpage and the tool is called Gobuster( a tool used for directory and file brute forcing)

**`gobuster dir -u targetmachineipaddress -w /usr/share/wordlists/dirb/common.txt`**

- **`dir`**: Specifies the mode of operation. In this case, it indicates that you i am performing directory brute-forcing.
- `-u`: Specifies the target URL.
- `-w`: Specifies the wordlist to be used for brute-forcing.
- `/usr/share/wordlists/dirb/common.txt`: This is an inbuilt wordlists that’s always on linux machines.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/da27d35b-1115-4326-85c8-571a2f8f96a1/Untitled.png)

from the above i found another webpage which is http://10.10.85.5/flag

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/3f20c59e-91cd-49d0-a7c5-555bd1c1bd02/Untitled.png)

i opened the flag directory and found two text file inside

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/c25a636a-74a4-4ee3-8290-e82504b9ae17/Untitled.png)

flag.txt showed me my third flag which is **{Fl4g_Fl4g_Fl4g}**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/61a7612a-b39f-4bfe-8af6-fd1c3e201ef7/Untitled.png)

flag2.txt showed an encoded text in Base64

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/29996a13-b040-4a40-a4e9-55ed71ee8c0c/Untitled.png)

i then used the command `echo e0ZsNGcyX2ZsNGcyX2ZsNGcyfQ== | base64 -d` and my Fourth flag is **{Fl4g2_fl4g2_fl4g2}**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/7b67e28e-9e94-45be-9a37-cd8b4e874e6a/Untitled.png)

i went back to my gobuster result and found one more accessible webpage which is 10.10.85.5/robots.txt. and behold when i opened the page, i found my fifth webpage flag **{Robots_Flag}**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/0a4da19f-ce03-4d63-92da-14d48122d22f/Untitled.png)

looking at the result from the robots.txt page i found the /hide.html so i proceeded to the page and i found my Sixth webpage flag **{H1d3_Fl4g}** 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/cbe56ce7-1a91-4bfc-8d08-53c255d1001e/Untitled.png)

from the above image the hide.html wasn’t displayed in the results supplied by gobuster and i still have two flags left to find. this kind of depicts that there are still some hidden html pages and txt files not displayed by go buster. so in other to display this, i would use the command: `gobuster dir -u targetmachineipaddress -w /usr/share/wordlists/dirb/common.txt -x html,txt`

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/86b1d900-a5bd-4498-ba83-149c0d44ad63/Untitled.png)

from the above, i found two new files which are index2.html and secret.txt. i opened the index2.html page and found my Seventh Flag **{C0nf1gur4t10n_Fl4g}**.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/acb6a64d-61c4-44f0-be97-6ffdfd6951e8/Untitled.png)

opened the secret.txt page and the Eight flag **{S3cr3t_Fl4g}** was there waiting for me

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/434903df-1abc-46f3-abef-bda600af0a09/Untitled.png)

The above exercise took a lot of trials and errors which if included in this documentation would make it cumbersome, but it was a wonderful experience and i love every aspect of it, there is another method of getting all the above flags using commands on my Linux machine, but i find the above more interesting as i had to learn outside the box, so i would show you the other method.

i used the find command to look up html directories, the i cd into the /var/www/html directory, this was where i used the command `ls -lah` which showed me all the folders & text i shared earlier

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/46c80ab0-ab1c-4819-b3e2-6f04af72d1e0/Untitled.png)

## STEP 8: Hash Cracking

i navigated to the ctf directory and opened the hash_to_crack folder, my hash texts and wordlists are in this folder, but user ctf doesn’t have adminsitrative access to install some of the tools which i need to crack the hash. this made me use the command `python3 -m http.server` to enable me download files from ctf to my machine. i used the `wget http://ctfipaddress:8000/filetobedownloaded` on my personal machine. 

it can be noted that ctf machine recognized my download attempts and registered my ip address and the documents i was able to retrieve from it’s machine.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/e35273e0-d1f0-4fcd-b24d-bddb31ba7973/Untitled.png)

now that i have all the documents i need on my machine let’s go Hashing. first thing i do is get the hash type, i can use various commands like `cat hashfile | hashid` , `echo $(<hashfile) | hashid` , `hashid -m $(cat hashfile)`. learning how to do hash identification in three different ways was awesome. from the below i deduced that the hash type is MD5. now i can use john the ripper.

Hash 1:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/faa3296b-e5a6-4641-ba8c-f3acf5cebb7e/Untitled.png)

from the result below the password for for hash1.txt is {C0d3_0b5cur3r_Flag} and this is our first hash flag.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/85d46f59-2c07-4808-a866-6124abd62fd9/Untitled.png)

Hash 2:

using the command `echo $(<hashfile) | hashid` to analyze the hash type

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/08784e55-dc65-408f-8aef-2a67233e3ef4/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/7893e5a2-27c8-421f-b136-8c05efcb507d/Untitled.png)

my Second hash flag is {C0d3_5l4y3r_Flag}

Hash 3:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/d1ba8e0f-3eb3-488b-b6bb-6c2c65d96afb/Untitled.png)

Hash 4:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/63cecca4-b1b0-4766-90e0-e7af74a99532/242fec38-6b14-48c0-a55d-276563be8c97/Untitled.png)

Hash 5:
https://www.notion.so/MY-FIRST-CYBERSECURITY-CAPTURE-THE-FLAG-CTF-ACTIVITY-AT-MASTERSCHOOL-4f3aa0e988d44551969972798c178140?pvs=4#932746a3fbf140d5b29f6951540afc15
