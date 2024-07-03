# AOS_Project1

Github steps:

* Create an account
* Generate an SSH key on the server:
  * https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
* Add this SSH key to your github account
  * https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
  * https://github.com/settings/keys

https://git-scm.com/docs/gittutorial


```
[rmodak@linux11112 ~]$ ssh-keygen -t ed25519 -C "sas999modak111@gmail.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/rmodak/.ssh/id_ed25519): 
Created directory '/home/rmodak/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/rmodak/.ssh/id_ed25519
Your public key has been saved in /home/rmodak/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:rTmuI0xTcxtw5BFuZg8BOoMjqRMGpq0fZaRseW1+lxY sas999modak111@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|..  . .o=.       |
|++ = o.o.o       |
|=.O B ooB E      |
|o= = =o+o+ o     |
|+ .  ..oSo*      |
| o .o  ..=       |
|  .o .  +        |
|    o .. .       |
|     ..o.        |
+----[SHA256]-----+
[rmodak@linux11112 ~]$ ^[[^C0~cat ~/.ssh/id_ed25519.pub~
[rmodak@linux11112 ~]$ cat ~/.ssh/id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKMCpDerpm6AsaNoIMD7M90trBK1wn40LhWl3I1SZ72I sas999modak111@gmail.com
[rmodak@linux11112 ~]$ ^C
[rmodak@linux11112 ~]$ ls -l
total 4
drwx------. 2 rmodak dip   10 Jul  3 09:30 Desktop
drwx------. 2 rmodak dip   10 Jul  3 09:30 Documents
drwx------. 2 rmodak dip   10 Jul  3 09:30 Downloads
drwx------. 2 rmodak dip   10 Jul  3 09:30 Music
drwx------. 2 rmodak dip   10 Jul  3 09:30 Pictures
drwx------. 2 rmodak dip   10 Jul  3 09:30 Public
-rw-------. 1 rmodak dip 1629 Oct  5  2022 sqlnet.log
drwx------. 2 rmodak dip   10 Jul  3 09:30 Templates
drwx------. 2 rmodak dip   10 Jul  3 09:30 Videos
[rmodak@linux11112 ~]$ cd Documents/
[rmodak@linux11112 Documents]$ ls -l
total 0
[rmodak@linux11112 Documents]$ ls -l
total 0
[rmodak@linux11112 Documents]$ cd Dow
bash: cd: Dow: No such file or directory
[rmodak@linux11112 Documents]$ cd
[rmodak@linux11112 ~]$ l-l
bash: l-l: command not found...
[rmodak@linux11112 ~]$ ls -l
total 4
drwx------. 2 rmodak dip   10 Jul  3 09:30 Desktop
drwx------. 2 rmodak dip   10 Jul  3 09:30 Documents
drwx------. 2 rmodak dip   33 Jul  3 10:06 Downloads
drwx------. 2 rmodak dip   10 Jul  3 09:30 Music
drwx------. 2 rmodak dip   10 Jul  3 09:30 Pictures
drwx------. 2 rmodak dip   10 Jul  3 09:30 Public
-rw-------. 1 rmodak dip 1629 Oct  5  2022 sqlnet.log
drwx------. 2 rmodak dip   10 Jul  3 09:30 Templates
drwx------. 2 rmodak dip   10 Jul  3 09:30 Videos
[rmodak@linux11112 ~]$ cd Downloads/
[rmodak@linux11112 Downloads]$ ls -l
total 4
-rw-r--r--. 1 rmodak dip 1195 Jul  3 10:06 forktest.rtf
[rmodak@linux11112 Downloads]$ cat forktest.rtf 
{\rtf1\ansi\deff0\nouicompat{\fonttbl{\f0\fnil\fcharset0 Courier New;}}
{\*\generator Riched20 10.0.22621}\viewkind4\uc1 
\pard\f0\fs22\lang1033 #include  <stdio.h>\par
#include  <unistd.h>\par
#include  <sys/wait.h>\par
\par
\par
\par
int  main()\par
\{\par
    printf("Parent: Process started\\n");\par
    printf("Parent: Forking a child.\\n");\par
    \par
    if (fork() != 0) \{\par
        // Parent\par
        int status;\par
        printf("Parent: Wait for child to complete.\\n")    ;\par
        // waitpid(pid, &status, options)\par
        // pid == 0 means wait for child whose \par
        // group-id = its calling process group-id\par
        waitpid(0, &status, 0);\par
        printf("Parent: Terminating.\\n");\par
    \}\par
    else \{\par
        // Child\par
        printf("Child: Process started.\\n");\par
        printf("Child: Start 10 second idle:");\par
        \par
        int i;\par
        for (i = 10; i >= 0; i--) \{\par
            printf("%3d", i); fflush(stdout);\par
            sleep(1);\par
        \}\par
        printf(" done!\\n");\par
        printf("Child: Terminating.\\n");\par
    \}\par
\}\par
\par
}
[rmodak@linux11112 Downloads]$ rm forktest.rtf 
[rmodak@linux11112 Downloads]$ ls -l
total 4
-rw-r--r--. 1 rmodak dip 695 Jul  3 10:07 forktest.c
[rmodak@linux11112 Downloads]$ ls -kl
total 4
-rw-r--r--. 1 rmodak dip 695 Jul  3 10:07 forktest.c
[rmodak@linux11112 Downloads]$ gcc forktest.c -o forktest
forktest.c:7:1: warning: return type defaults to ‘int’ [-Wimplicit-int]
    7 | main()
      | ^~~~
[rmodak@linux11112 Downloads]$ vim forktest.c 
[rmodak@linux11112 Downloads]$ gcc forktest.c -o forktest
[rmodak@linux11112 Downloads]$ ./forktest
Parent: Process started
Parent: Forking a child.
Parent: Wait for child to complete.
Child: Process started.
Child: Start 10 second idle: 10  9  8  7  6  5  4  3  2  1  0 done!
Child: Terminating.
Parent: Terminating.
[rmodak@linux11112 Downloads]$ ls -l
total 24
-rwx------. 1 rmodak dip 17808 Jul  3 10:08 forktest
-rw-r--r--. 1 rmodak dip   694 Jul  3 10:08 forktest.c
[rmodak@linux11112 Downloads]$ cd ..
[rmodak@linux11112 ~]$ ls -l
total 4
drwx------. 2 rmodak dip   10 Jul  3 09:30 Desktop
drwx------. 2 rmodak dip   10 Jul  3 09:30 Documents
drwx------. 2 rmodak dip   50 Jul  3 10:08 Downloads
drwx------. 2 rmodak dip   10 Jul  3 09:30 Music
drwx------. 2 rmodak dip   10 Jul  3 09:30 Pictures
drwx------. 2 rmodak dip   10 Jul  3 09:30 Public
-rw-------. 1 rmodak dip 1629 Oct  5  2022 sqlnet.log
drwx------. 2 rmodak dip   10 Jul  3 09:30 Templates
drwx------. 2 rmodak dip   10 Jul  3 09:30 Videos
[rmodak@linux11112 ~]$ cd Documents/
[rmodak@linux11112 Documents]$ ls -l
total 0
[rmodak@linux11112 Documents]$ git clone git@github.com:Rimcode-ai/AOS_Project1.git
Cloning into 'AOS_Project1'...
The authenticity of host 'github.com (140.82.116.4)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
[rmodak@linux11112 Documents]$ ls -l
total 0
drwx------. 3 rmodak dip 45 Jul  3 10:10 AOS_Project1
[rmodak@linux11112 Documents]$ cd AOS_Project1/
[rmodak@linux11112 AOS_Project1]$ ls -l
total 4
-rw-------. 1 rmodak dip 14 Jul  3 10:10 README.md
[rmodak@linux11112 AOS_Project1]$ cp ~/Downloads/forktest.c 
cp: missing destination file operand after '/home/rmodak/Downloads/forktest.c'
Try 'cp --help' for more information.
[rmodak@linux11112 AOS_Project1]$ cp ~/Downloads/forktest.c .
[rmodak@linux11112 AOS_Project1]$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	forktest.c

nothing added to commit but untracked files present (use "git add" to track)
[rmodak@linux11112 AOS_Project1]$ git add forktest.c 
[rmodak@linux11112 AOS_Project1]$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   forktest.c

[rmodak@linux11112 AOS_Project1]$ git commit -m "forktest.c is the first AOS project"
[main 10e52ee] forktest.c is the first AOS project
 Committer: rima modak <rmodak@linux11112.dc.engr.scu.edu>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 31 insertions(+)
 create mode 100644 forktest.c
[rmodak@linux11112 AOS_Project1]$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
[rmodak@linux11112 AOS_Project1]$ git push 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 609 bytes | 304.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Rimcode-ai/AOS_Project1.git
   3f3f95c..10e52ee  main -> main
[rmodak@linux11112 AOS_Project1]$ git clone git@github.com:Rimcode-ai/AOS_Project1.git^C
[rmodak@linux11112 AOS_Project1]$
```
