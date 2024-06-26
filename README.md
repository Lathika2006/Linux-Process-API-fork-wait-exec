# Linux-Process-API-fork-wait-exec-
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

## C Program to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }


```
##OUTPUT

![Screenshot 2024-03-27 190058](https://github.com/Lathika2006/Linux-Process-API-fork-wait-exec/assets/148959215/97ef94a4-3c10-4fef-b437-a69ca986feda)

#$ps

![image](https://github.com/Lathika2006/Linux-Process-API-fork-wait-exec/assets/148959215/88484f24-5add-47a0-bd44-09777dcee24a)

## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdio.h>
#include<stdlib.h>
int main()
{ 
int pid; 
pid=fork(); 
if(pid == 0) 
{ 
printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); 
} 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);
} 
}
```
##OUTPUT

![image](https://github.com/Lathika2006/Linux-Process-API-fork-wait-exec/assets/148959215/df497d37-d21e-4a13-a572-9ecc11628a12)



## C Program to execute Linux system commands using Linux API system calls exec() family

```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{
        int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                printf("child did not exit successfully\n");
                printf("Done.\n");
                printf("Running ps with execlp. Now with path specified\n");
                execlp("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                printf("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);
}
```
##OUTPUT

![Screenshot 2024-03-27 185823](https://github.com/Lathika2006/Linux-Process-API-fork-wait-exec/assets/148959215/23d6b25d-b9f2-4c7d-b336-448ce857fb8e)

![Screenshot 2024-03-27 185910](https://github.com/Lathika2006/Linux-Process-API-fork-wait-exec/assets/148959215/6a2c5bca-3557-45b7-b413-99ffdf1c412b)

# RESULT:
The programs are executed successfully.
