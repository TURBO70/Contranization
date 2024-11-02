

- Every operating system has kernel mode and user mode, and it needs kernel mode to manage the hardware. But does it need user mode?
![[Pasted image 20241016072445.png]]

- Every physical machine or virtual machine (VM) has its own hardware and operating system. From the management software, you can create virtual machines.

- in this way, I can avoid needing a license for every VM I create, and I also reduce costs because there's no need for updates for every OS in each VM.

- All of this happens because I rely on the VM's kernel mode or the physical machine's kernel mode.



## Containers:

#### Virtual machine

- Something to note is that the kernel is unchangeable (the Linux kernel is the same across all Linux distributions).
![[Pasted image 20241016073754.png]]

- Every container fully relies on the kernel, but it needs to add some OS-specific elements (a few things from user mode).

- I build the container down-up starting from the OS-specific to the App every layer in the middle is called layers (this layers can be changed files or libraries or any thing).
