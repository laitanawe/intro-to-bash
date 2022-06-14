---
title: "Working on a remote HPC system"
teaching: 25
exercises: 10
questions:
- "What is an HPC system and how does it work?"
- "How do I connect to a remote HPC system?"
objectives:
- "Understand how ssh and related tools are used to connect to a remote HPC system."
- "Understand the general HPC system architecture."
keypoints:
- "An HPC system is a set of networked machines."
- "HPC systems typically provide login nodes and a set of worker nodes."
- "The resources found on independent (worker) nodes can vary in volume and
  type (amount of RAM, processor architecture, availability of network mounted
  filesystems, etc.)."
- "Files saved on one node are available on all nodes."
- "ssh is the preferred way to connect to Linux servers"
- "ssh is secure and protects information sent"
- "sftp is available in a command line application and in GUI based applications for file transfers"
---

## What Is an HPC System?

The words "cloud", "cluster", and the phrase "high-performance computing" or
"HPC" are used a lot in different contexts and with various related meanings.
So what do they mean? And more importantly, how do we use them in our work?

The *cloud* is a generic term commonly used to refer to computing resources
that are a) *provisioned* to users on demand or as needed and b) represent real
or *virtual* resources that may be located anywhere on Earth. For example, a
large company with computing resources in Brazil, Zimbabwe and Japan may manage
those resources as its own *internal* cloud and that same company may also
use commercial cloud resources provided by Amazon or Google. Cloud
resources may refer to machines performing relatively simple tasks such as
serving websites, providing shared storage, providing web services (such as
e-mail or social media platforms), as well as more traditional compute
intensive tasks such as running a simulation.

The term *HPC system*, on the other hand, describes a stand-alone resource for
computationally intensive workloads. They are typically comprised of a
multitude of integrated processing and storage elements, designed to handle
high volumes of data and/or large numbers of floating-point operations
([FLOPS](https://en.wikipedia.org/wiki/FLOPS)) with the highest possible
performance. For example, all of the machines on the
[Top-500](https://www.top500.org) list are HPC systems. To support these
constraints, an HPC resource must exist in a specific, fixed location:
networking cables can only stretch so far, and electrical and optical signals
can travel only so fast.

The word "cluster" is often used for small to moderate scale HPC resources less
impressive than the [Top-500](https://www.top500.org). Clusters are often
maintained in computing centers that support several such systems, all sharing
common networking and storage to support common compute intensive tasks.

---
# SSH Basics
​
**The take home from this lesson.**
​
- Use the command `ssh <username>@<remote server IP address|domain name>` to connect to a remote server.
​

**The details on how ssh works.**
​
- The (local) client asks the remote server (sumhpc login node) to establish a connection.
- The server and the client work together to encrypt the contents of data transfered through the connection.

---
**Using ssh to connect to remote server.**
​
- Open the terminal
​
- Type `ssh <username>@<remote server IP address|domain name>` where username is your username on the remote system and the IP address or domain name (that resolves to an IP address) to the remote system that you would like to connect to.  


**Example ssh connection for this class.**
​
- Open the terminal
​
- Type `ssh user@<remote server IP address>` where ```user``` is your username on the remote system for this example. If you don't know it already, you can ask the instructor to provide you remote IP address. Your username is user for this example.
​
- Notice the first time you connect to a new machine you may get asked the following question. ​

```BASH
[user@edu-vm-63d1410f-2 ~]$ ssh user@35.227.70.171
The authenticity of host '35.227.70.171 (35.227.70.171)' can\'t be established.
ECDSA key fingerprint is SHA256:UTHv5IOvrF9uvxuh9Fo8uW2bx0BwCRLyrwHhONoiIj8.
ECDSA key fingerprint is MD5:15:bb:25:2a:3a:45:f4:c7:df:21:26:37:12:66:79:77.
Are you sure you want to continue connecting (yes/no)?
```
- If this is the system that you are looking to connect and you trust it, then type `yes`.
​
- Now your connected to the remote system things that you enter in the terminal are now being exicuted on the remote system.

---
# SFTP
​
SFTP stands for secure file transfer protocol and it is used to transfer files from one computer to another. Some commony used sftp client applications include CyberDuck, FileZilla, MobaXterm and WinSCP. You can contact your desktop or laptop system admistartor for information regarding the installation of an sftp client.
​
MobaXtem will automatically establish and an sftp session when ssh'ing into a remote system. It is visible as a yellow globe on the left hand side of the MobaXterm terminal. 
​
Now we will do a live example of establishing a separate sftp connection to the remote server.

{% include links.md %}
