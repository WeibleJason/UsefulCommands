# Docker: The Basics

Before understanding what Docker is, it's worth knowing why Docker is great.
After a little history and background, this guide will walk through getting
up and running with Docker starting with a basic Dockerfile, but assuming
you know how to install Docker and navigate your computer.

## History of Docker: A Problem Needs Solved
Have you ever tried to build an app at a hackathon or with some friends, agreed to use
Python, find out three of you are using Python 3, the other three are using Python 2,
three of you are on MacOS, one of you is using Ubuntu, and the other two are on Windows.
After agreeing to use Python 3, spend 20-30 minutes installing everything so that 
everyone is using the same langauge, a total of one hour has passed since the group of
you got together and nothing has been accomplished. As you're developing, if any
library gets updated or deprecated, the group of you now have to go through a process
of individually updating everything to make sure the environment is the same.

This process is a time sink and becomes incredibly time consuming for developers, whose
time is best spent actually developing, not getting things ready to be developed. 

Before Docker, the best way to solve this problem was with virtual machines.

## Virtual Machines: A Heavy Solution
Virtualization addresses the problem of everyone individually having to ensure their
individual machine can build, boot, load, install, configure, and connect to everything
involved with whatever app you're working on. Having a developer individually check off
these tasks each time something in the process has updated is a tedious waste of time.

Virtual machines, or VMs, are a solution to this tedious development headache, but they
are not without flaws. Without going to much into what VMs actually are, they're
essentially resource intensive, isolated computing environments that exists on your 
existing computer as a virtual copy of some other machine you're trying to emulate. The
reason VMs are a solution to the developer headache above is that as long as someone else
is able to make their own virtual copy of that same emulated environment, they will be
able to run the app that is being worked on.

So problem sovled?

Not exactly. For this developer headache to be solved, every developer on the
project would have to be using the same VM environment. This solution is essentially
solving the problem by forcing anyone who wants to work on the project to setup their
own copy of the VM. Setting up VMs isn't too bad if you have a strong computer and only
need to set up the environment once. Unfortunately, this is unrealistic to the current
state of software development.

Additionally, VMs are heavy. Even on high end machines, they can be slow to use and
require you to partition away your computing resources between multiple operating
systems at the same time. 

## Containers: Share the OS, not the Hardware
Containers, a type of virtualization, share resources at the operating system
level, not the hardware level. This new way of sharing is much faster since you 
don't have to divide up the resources at the hardware level. Almost everything about
containers is faster than VMs.

Taking a black box approach, starting a VM is equivalent to taking your current black box
and dividing it into two different black boxes. Containers are equivalent to giving
a bunch of commands to your current black box, which is able to maintain its original
identity. 

## Docker: Don't share too much
The last thing you would want to do if you were sharing resources across your OS is lose
track of what's being shared with what. Docker is a program that manages what's being
shared by bundling everything into their own individual containers. This exclusivity
means that I can have one environment, with all its libraries, dependencies, file paths,
etc., in one Docker container, with a completely different container with different
libraries, different dependencies, and different file paths, both on the same machine.
You don't have to partition any physical resources. Everything is managed at the OS
level. Even more important, you can share the environment of these containers simply by 
sharing a file. Now instead of having to hope a colleague has the same environment as you
or having to hope they can run the same VM on their machine, you can just share something
called the Dockerfile, which is a script like text file that can be used to build the
same exact environment. 

## Docker: Dockerfiles, Images, Containers
Now for some terminology.
- Container: A Docker container is an instance of a Docker image. It is the thing that
you need to have running to really make use of Docker. 
- Image: A Docker image is considered the template for a Docker container. To start a
container, you need to create the container from the image, and then run the container.
Images can be stored in either a local or remote repository, like Dockerhub, which
allows you to share images.
- Dockerfiles: A Dockerfile is a script like file that can be used to build a Docker
image. You can think of it like the template for a Docker image. Wait, does that mean
the Dockerfile is a template for a template? Yes, however Dockerfiles are relatively
small (a simple text file) compared to a Docker image (easily 100+ MB). So sharing
Dockerfiles is way easier than sharing Docker images.

## Docker: Too Good to be True?
Docker ins't perfect. One of the best aspects of Docker is how quick it's able to get a
duplicate environment up and running. However, if you want to actually develop *inside*
the container, you're going to have to install whatever editor, syntax highlighters, etc.
you want to use inside the container. Doing so isn't that big of a problem as long as
you're continuing to use Docker like it's a VM where you write a Dockerfile that sets
up your environment, including all the personal tools you might want. And if you want
to share your Dockerfile, you'll have to ask others to edit the Dockerfile for
themselves, which somewhat defeats the purpose. 

So what exactly is Docker being used for? Docker is used for as the building environment
for whatever you're developing. It doesn't mean that you have to actual write from inside
the environment. Like a VM, you can mount directories every time you run a container.
This mounting allows you to separate the environment from the actual project, being
able to share each individually.

## Enough talk: Show me the code
Once you have Docker running, create an empty directory. Documentation for Docker
recommends putting each Dockerfile into an empty directory, along with any
additional files you need for building.

Using your OS CLI, navigate to the directory containing the Dockerfile and type
```bash
docker build .
```
This will build a Docker image based on the Dockerfile in the directory.
If successful, you will see the new image in the list of Docker you have by typing
```bash
docker images
```

Now that the Docker image is created, we can mount a directory and run the container at
the same time. To do this on Windows, type
```bash
docker run -it --volume /c/path/to/dir/on/Windows/directory:/path/to/where/dir/goes/in/containter repository/image shell
```

The above command will mount a directory on a Windows machine to a Linux based machine.
For example
```bash
docker run -it --volume /c/Users/Jason/Desktop/CSE3341/Project1:/home/cse3341/project1 weible/osu_cse bash
```

This example will mount Project1 on the Windows machine inside the linux based container
with name 'weible/osu_cse' at the location specfieid after the colon and launch that
container with the bash shell. 

From here, you edit files inside the mounted directory while on the Windows machine, then
run and build from inside the container environment. 



