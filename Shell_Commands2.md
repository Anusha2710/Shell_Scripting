-- Lets execute the file now 

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/49562769-a0be-4551-8a9d-0f13e99a1eca)

- we can also execute by using "./" as (./my-first-shell-script.sh)
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/be01afea-e62a-4492-a0f0-bcb969baab74)

15. chmod command
- to enable this we need to enable permission
- using "chmod" (user, group, everyone)
                (4- read, 2- write, 1- execute)
                (eg- chmod 444 = we are giving read permission to user,group nd everyone)
- Now, we need to give all permissions in order to use ./
> chmod 777 my-first-shell-script.sh    ( which means 4+2+1=7)
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/513fa5ed-bba7-423a-9461-7e5d7c4fa0c5)

16. Shell Script1:
- Now, lets write a shell script to create a folder, and 2 files inside the folder everytime when script is executed, we'll also change permissions of file.
> vi sample-shell-script.sh
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/1037f673-8d42-45b3-afd8-679ed98bc718)

- lets give permissions now
> chmod 777 sample-shell-script.sh
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/5807ced4-70fd-4ddb-b3c8-3a2cd3c856cd)

17. Shell Script2:
- Now, lets write a shell script to check the Node Health of our VM.
> vi node-health.sh
1- set -x = command is used to debug bash script where every executed statement is printed to the shell for debugging.

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/cd544a91-e5f0-4fc0-a61e-8787c1cd1874)

- Lets execute the script

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/361fabf4-7500-4eae-8fef-5fa3e185faec)

2- set -e = aborts the execution of a command and returns the exit status code of the command that failed.

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/3f5382ed-8632-4849-88dc-958ce902fedb)

- Lets execute the script

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/d953f99a-5aaa-4c14-88a1-31db74cf9262)

- But, when we add pipe statements

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/2bbc1cb1-6fe1-412d-aff1-740e6aa9c3d5)

- Then set -x does work, instead it executes the script without aborting the failed command i.e; it only considering last statements in script with pipe, it's just ignoring first statement

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/4be3e305-a09d-47d2-8d3d-34d059dcd2ff)

- To overcome with we are going to use "set -o pipeline" command

3- set -o pipeline

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/e3256f23-d82f-468a-89dd-02ee1905b3d7)

- Lets execute it aborts and throws error now.

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/4b0f7c88-272b-4a0d-b78a-da2f9c4da470)

18. Shell Script3:
- Now, Lets say in Amazon Company a developer has deployed 200 micro services, where each app uses different processes.

1- We need to find the processes running by "amazon" keyword 

> ps -ef | grep "amazon"
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/9be821ac-1d06-4027-bf91-f90ad2532e12)

Here,  ps -ef = prints processes in full format,
       grep = filter the output with specific keyword,
       pipe = get output from first command and send it to second command

2- We need only process ids of "amazon" processes

> ps -f | grep "amazon" | awk -F" " '{print $2}'
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/f7fd9594-7cdf-4ed8-bef6-2f4163e9d68b)

Here, awk = prints output in specific column (here we are printing data in 2nd column)

eg:
Lets create a test file now, try to print my name here

![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/288f9a51-683b-49c6-90de-3bef482c6ead)

Lets try using GREP command, it prints the entire line

![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/a29e246e-fd41-47d9-92ab-a373bf26739c)

 Lets try using GREP with AWK, now it gives only my name


19. DATE- Shell Script4 (Imp Interview Question):
- If we use date command, it prints todays date

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/2696acfe-0095-4fd2-bb9e-ff129485bc7b)

- But, if we use date command with echo, it prints only keywords present in echo, but not the actual command

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/20c7341f-0b37-426a-a0c0-dbf08057b81c)
- Because, date is a system default command, it sends output to stdin, as pipe works only if it passes the info to next command but not stdio i.e: echo

20. CURL vs WGET:

- In every company whenever an application is failing we go to log file and check the errors
- Lets upload the log files to external storage i.e; github
- Here, we use CURL command - retrieves the info from internet

![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/427b10f1-c914-4029-942d-7312c816a663)
here we simply used curl along with grep command

- we can also use [curl -X GET api.(name)] to get the info from this api

- Here, we can also use WGET command - it downloads the file
- As file is downloaded, we need to use "cat" command to display contatent along with grep to search the pattern

![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/ff3a51d6-f22a-47d7-abf2-dab2d99b4dee)

So, using CURL we are using 1 command and WGET 2 commands
If we dont want to download files and only display contents we use CURL, and if we want to download file in local disk we use WGET here.

21. FIND command:

- if we want to find any file in any of the directories we use FIND command.
- suppose we want to find this file
  ![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/a36f1ad4-2fbe-4d7a-aec6-e997451868b5)

  - use SUDO command infront of file command
  ![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/10def126-7d92-4c70-922c-d3afad92dff5)

- here, sudo is the root user, we are granting permission to access root user as the directories 
- if we want to switch user we use this command below
  ![image](https://github.com/Anusha2710/Shell_Scripting/assets/47424821/1144bc27-e1e8-42d7-8844-58801032b355)















