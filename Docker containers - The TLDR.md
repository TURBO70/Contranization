
- A container is the runtime instance of an image.
- Instead of running a full-blown OS like a VM, containers share the OS/kernel with the host they’re running on.
- A single Docker image can be used to start multiple Docker containers.

![[Pasted image 20241102215934.png]]

- `docker container run <image> <app>`
- `$ docker container run -it ubuntu /bin/bash`
- `$ docker container run -it alpine:latest sleep 10`

To stop the container:  
`docker container stop`

To start the container:  
`docker container start`

To delete a container forever:  
`docker container rm`

## Docker containers - The deep dive

### Containers vs VMs

**VMs Architecture**
![[Pasted image 20241102220037.png]]


**Containers Architecture**

![[Pasted image 20241102220108.png]]

### The major difference between the VM's and the Containers:

- Hypervisors perform **hardware virtualization** — they carve up physical hardware resources into virtual versions called VMs.
- Containers perform **OS virtualization** — they carve OS resources into virtual versions called containers.

### Container lifecycle

**Change the name of the running container**  
`$ docker container run --name sawsan -it ubuntu:latest /bin/bash`

**Write data to container**  
`# cd tmp`  
`# echo "Jan 25th, the day Egypt stood still" > newfile`  
`# ls -l`  
`# cat newfile`

**Stop containers**  
`docker container stop <container-id or container-name>`

**Start containers**  
`docker container start <container-name>`

**Start containers in detached mode (run it in the background)**  
`docker container run -d <container-name>`

**Connect to running container**  
`docker container exec -it <container-name> bash`

**Try to access the text file created (newfile) after restarting and reconnecting to the container**

**Notes**

1. The data created in this example is stored on the Docker hosts local filesystem. If the Docker host fails, the data will be lost.
2. Containers are designed to be immutable objects and it’s not a good practice to write data to them

**Kill a running container**

- In one step:
    - `docker container rm -f <container-name>`
- In two steps:
    - `docker container stop <container-name>`
    - `docker container rm <container-name>`

### Stopping containers gracefully

- `docker container stop` sends a **SIGTERM** signal to PID(1)
- If the process doesn't exit in 10 sec it sends a **SIGKILL** signal



## Containers - The commands

- `docker container run` // start new containers.
- `docker container run -it ubuntu /bin/bash`
- `Ctrl-PQ` // will detach your shell from the terminal of a container and leave the container running (UP) in the background.
- `docker container ls` // lists all containers in the running (UP). Add -a flag to list (Existed) containers.
- `docker container exec` // runs a new process inside of a running container.
- `docker container stop` // stop a running container and put it in the Exited (0) state.
- `docker container start` // will restart a stopped (Exited) container.
- `docker container rm` // delete a stopped container.
- `docker container stop` // stops a running (UP) container .
- `docker container inspect` // will show you detailed configuration and runtime information about a container.