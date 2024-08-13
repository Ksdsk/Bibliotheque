## What is it?
Docker is an operating system for containers. Similar to how a virtual machine virtualizes server ahrdware, containers virtualize the operating system of a server ([What is Docker? | AWS (amazon.com)](https://aws.amazon.com/docker/#:~:text=Docker%20is%20an%20operating%20system,%2C%20start%2C%20or%20stop%20containers.)).
## Containers
A container is the standard unit of software that packages up code and all of its dependencies so the application runs quickly and reliably from one computing environment to another ([What is a Container? | Docker](https://www.docker.com/resources/what-container/)). It's designed to be lightweight and *standalone*, such that it can be easily transported into another environment safely. This makes containers almost like an engine for a portable program.

Because the containers *virtualize the operating system*, there are some key differences between itself and a virtual machine:
- Containers
	- Abstraction of the application layer that packages code and dependencies together.
	- High iteration speed