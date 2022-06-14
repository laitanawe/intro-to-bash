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
---
**The details on how ssh works.**
​
- The (local) client asks the remote server (sumhpc login node) to establish a connection.
- The server and the client work together to encrypt the contents of data transfered through the connection.

{% include links.md %}
