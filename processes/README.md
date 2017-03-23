# Processes

# What a process is?
# How does the Kernel manage existing processes?
# Creating a new process in UNIX
# Relation between processes and files

![Files and Processes](./files_processes.png)
![Files and Processes after a `fork()`](./file_processes_after_fork.png)


After creating a new process with `fork()` this picture illustrate the situation of parent and child processes

As seen, parent and child processes share the same entry on the open files table. This means, they both share the same offset on the file. When one of them writes (with `write()`) the offset will get modified then for both. The next `write()` operation perform by any of the two processes will be relative to the newly set offset. The following code can be executed to illustrate this effect. In this program, a child process is created. Right after creation, the child is somehow forced to leave the CPU by using `sleep()`. The parent process will most probably be chosen for execution within these 5 seconds, writting the "parent" on the file. When the 5 seconds consume, the child will at some point also chosen for execution and will write "child" on the file right after the word parent. 

```c
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <errno.h>

int main(int argc, char **argv) {

	int fd = open("example_file",O_CREAT|O_WRONLY|O_TRUNC,0666);
	if (fd == -1)
		printf("The file example_file couldn't be opened. Error reported: %d\n",errno);

	if (fork()==0) {
		// child code goes here
		sleep(5); // forces the child out of the cpu
		write(fd,"child",strlen("child"));			
	} else {
		// parent code goes here
		write(fd,"parent",strlen("parent"));
		wait(NULL);
	}
	close(fd);
}
```
