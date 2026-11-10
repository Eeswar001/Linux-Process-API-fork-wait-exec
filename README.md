[# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls


#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main()
{
    int pid = fork();

    if (pid == 0)
    {
        printf("I am the child process.\n");
        printf("Child PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    }
    else if (pid > 0)
    {
        printf("I am the parent process.\n");
        printf("Parent PID: %d\n", getpid());

        wait(NULL);

        printf("Child process has finished.\n");
    }
    else
    {
        perror("fork failed");
        return 1;
    }

    return 0;
}



##OUTPUT

<img width="855" height="248" alt="Screenshot 2026-10-22 221428" src="https://github.com/user-attachments/assets/981f4213-3be1-46aa-8a5c-f5a37fe7008f" />








## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family


#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main()
{
    int pid = fork();

    if (pid == 0)
    {
        printf("Child process is executing ls command.\n");
        fflush(stdout);

        execlp("ls", "ls", (char *)NULL);

        perror("exec failed");
        exit(1);
    }
    else if (pid > 0)
    {
        wait(NULL);
        printf("Child process completed.\n");
    }
    else
    {
        perror("fork failed");
        return 1;
    }

    return 0;
}











##OUTPUT




<img width="892" height="260" alt="image" src="https://github.com/user-attachments/assets/342d40f6-2cfe-4595-83eb-277c74ea33ab" />















# RESULT:
The programs are executed successfully.
