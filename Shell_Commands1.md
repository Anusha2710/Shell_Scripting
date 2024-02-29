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

