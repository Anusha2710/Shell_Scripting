**###Shell-commands**

*purpose of Shell Scripting in DevOps:

- we use it for = Infra maintainance
                = code management (interact with git)
                = configuration management

*Usecase:

- For suppose john is a Devops engineer in Amazon
- We use to look over 10,000 VMs, he need to monitor node health of these VMs
- If any of VM doesn't work properly like, if there's issue with cpu or memeory
- Instead of looking into all VMs individually he will write a Shell script and saves in Git repo
- If any issue happens he will just execute shell script automatically in local machine and finds out he problem
- And if anything goes wrong it automatically sends mail that among 10,000 VMs (10 are suspicious, 5 less memory, 5 less cpu)

- How to get inside root user = sudo su -
- How to come otside root user = ctrl + d

1. man Command
> man ls = provides details of any command
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/125ca27e-7ee1-456e-a9eb-02d7ab61ea99)

2. pwd command
> pwd = present working directory

3. cd command
> cd anu/ = go inside the directory

> cd / = get out of the directory

4. ls command
> ls -ltr = view reverse output order by date (if its a directory it shows d, remaining all files)

5. touch command
> touch = create empty file

6. vi command
> vi test = create empty file (go inside file, click i for insert, after writing esc and :wq for saving file)

7. cat command
> cat test = view contents in file

8. rm command
> rm test = remove file

9. mkdir command
> mkdir anu = create directory

10. rm -r command
> rm -r = remove directory

11. free command
> free = memory of server
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/a5aa0234-d368-4b9c-a76e-3ae8a6607c49)

12. nproc command
> nproc =no. of cpu's
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/891bc58d-2797-4c47-807d-c1478d936149)

13. df -h command
> df -h = disk size
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/3be1a688-e034-47af-a648-3465c1e8c30e)

14. top command
> top = complete info of server (memory,cpu and all)
![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/76b2286f-1e3f-46b3-aca3-eb90c46f4019)

-- Lets create a file using shell script now

- create a file 
> vi my-first-shell-script.sh

- go inside the file
#!/bin/bash                 = first line in every file called (shebang)
                              - here 'bash' is executable

                              - we also use bash, dash, sh,ksh
                              - some people use 'sh' which redirects to 'bash' by linking concept

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/785ca91e-6d25-4134-8eeb-473acd2aa61d)

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

Here,  ps -ef = prints processes in full format
       grep = filter the output with specific keyword
       pipe = get output from first command and send it to second command

2- We need only process ids of "amazon" processes

> ps -f | grep "amazon" | awk -F" " '{print $2}'

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/f7fd9594-7cdf-4ed8-bef6-2f4163e9d68b)

Here, awk = prints output in specific column (here we are printing data in 2nd column)
       
19. Shell Script4 (Imp Interview Question):
- If we use date command, it prints todays date

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/2696acfe-0095-4fd2-bb9e-ff129485bc7b)

- But, if we use date command with echo, it prints only keywords present in echo, but not the actual command

![image](https://github.com/Anusha2710/AWS-Basics/assets/47424821/20c7341f-0b37-426a-a0c0-dbf08057b81c)
- Because, date is a system default command, it sends output to stdin, as pipe works only if it passes the info to next command but not stdio i.e: echo
