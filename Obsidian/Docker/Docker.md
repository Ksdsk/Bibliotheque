## What is it?
Docker is an operating system for containers. Similar to how a virtual machine virtualizes server ahrdware, containers virtualize the operating system of a server ([What is Docker? | AWS (amazon.com)](https://aws.amazon.com/docker/#:~:text=Docker%20is%20an%20operating%20system,%2C%20start%2C%20or%20stop%20containers.)).
## Containers
A container is the standard unit of software that packages up code and all of its dependencies so the application runs quickly and reliably from one computing environment to another ([What is a Container? | Docker](https://www.docker.com/resources/what-container/)). It's designed to be lightweight and *standalone*, such that it can be easily transported into another environment safely. This makes containers almost like an engine for a portable program.

Because the containers *virtualize the operating system*, there are some key differences between itself and a virtual machine:
- Containers
	- Abstraction of the application layer that packages code and dependencies together.
	- High iteration speed because it only contains high-level software.
	- Has a robust ecosystem sharing containers.
	- Potential security risk of infecting the shared host of the containers.
- Virtual Machine
	- Provides complete emulation of low-level hardware devices like CPU.
	- Provides full isolation security.
	- Much more dynamic and can be interactively developed.
	- More time consuming to build and regenerate.
	- VMs take up a lot of storage space.

The right answer for your tool will depend on the use case. If you are simply trying to launch a simple ecosystem of software-only projects, then containers might be the right option for you. If you have a specific hardware requirement for your projects, then likely you'll need a virtual machine. Of course, you could choose to employ both, but it is likely that you won't need to.
