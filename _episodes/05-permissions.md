---
title: "Permissions"
teaching: 10
exercises: 0
questions:
- "Understanding file/directory permissions"
objectives:
- "What are file/directory permissions?"
- "How to view permissions?"
- "How to change permissions?"
- "File/directory permissions in Windows"
keypoints:
- "Correct permissions are critical for the security of a system."
- "File permissions describe who and what can read, write, modify, and access a file."
- "Use `ls -l` to view the permissions for a specific file."
- "Use `chmod` to change permissions on a file or directory."
---

### Background

Unix controls who can read, modify, and run files using *permissions*.
We'll discuss how Windows handles permissions at the end of the section:
the concepts are similar,
but the rules are different.

Let's start with Nelle.
She has a unique [user name]({{ page.root }}/reference/{{ site.index }}#user-name),
`nnemo`,
and a [user ID]({{ page.root }}/reference/{{ site.index }}#user-id),
1404.

> ## Why Integer IDs?
>
> Why integers for IDs?
> Again, the answer goes back to the early 1970s.
> Character strings like `alan.turing` are of varying length,
> and comparing one to another takes many instructions.
> Integers,
> on the other hand,
> use a fairly small amount of storage (typically four characters),
> and can be compared with a single instruction.
> To make operations fast and simple,
> programmers often keep track of things internally using integers,
> then use a lookup table of some kind
> to translate those integers into user-friendly text for presentation.
> Of course,
> programmers being programmers,
> they will often skip the user-friendly string part
> and just use the integers,
> in the same way that someone working in a lab might talk about Experiment 28
> instead of "the chronotypical alpha-response trials on anacondas".
{: .callout}

### Permissions in Unix

Users can belong to any number of [groups]({{ page.root }}/reference/{{ site.index }}#user-group),
each of which has a unique [group name]({{ page.root }}/reference/{{ site.index }}#user-group-name)
and numeric [group ID]({{ page.root }}/reference/{{ site.index }}#user-group-id).
The list of who's in what group is usually stored in the file `/etc/group`.
(If you're in front of a Unix machine right now,
try running `cat /etc/group` to look at that file.)

Now let's look at files and directories.
Every file and directory on a Unix computer belongs to one owner and one group.
Along with each file's content,
the operating system stores the numeric IDs of the user and group that own it.

The user-and-group model means that
for each file
every user on the system falls into one of three categories:
the owner of the file,
someone in the file's group,
and everyone else.

For each of these three categories,
the computer keeps track of
whether people in that category can read the file,
write to the file,
or execute the file
(i.e., run it if it is a program).

For example, if a file had the following set of permissions:

<table class="table table-striped">
<tr><td></td><th>user</th><th>group</th><th>all</th></tr>
<tr><th>read</th><td>yes</td><td>yes</td><td>no</td></tr>
<tr><th>write</th><td>yes</td><td>no</td><td>no</td></tr>
<tr><th>execute</th><td>no</td><td>no</td><td>no</td></tr>
</table>

it would mean that:

*   the file's owner can read and write it, but not run it;
*   other people in the file's group can read it, but not modify it or run it; and
*   everybody else can do nothing with it at all.


Let's look at this model in action.
If we `cd` into the `labs` directory and run `ls -F`,
it puts a `*` at the end of `setup`'s name.
This is its way of telling us that `setup` is executable,
i.e.,
that it's (probably) something the computer can run.

~~~
$ cd labs
$ ls -F
~~~
{: .bash}
~~~
safety.txt    setup*     waiver.txt
~~~
{: .output}

> ## Necessary But Not Sufficient
>
> The fact that something is marked as executable
> doesn't actually mean it contains a program of some kind.
> We could easily mark this HTML file as executable
> using the commands that are introduced below.
> Depending on the operating system we're using,
> trying to "run" it will either fail
> (because it doesn't contain instructions the computer recognizes)
> or cause the operating system to open the file
> with whatever application usually handles it
> (such as a web browser).
{: .callout}







## Nelle's Pipeline: A Typical Problem

Nelle Nemo, a marine biologist,
has just returned from a six-month survey of the
[North Pacific Gyre](http://en.wikipedia.org/wiki/North_Pacific_Gyre),
where she has been sampling gelatinous marine life in the
[Great Pacific Garbage Patch](http://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch).
She has 1520 samples that she's run through an assay machine to measure the relative abundance
of 300 proteins.
She needs to run these 1520 files through an imaginary program called `goostats.sh` she inherited.
On top of this huge task, she has to write up results by the end of the month so her paper
can appear in a special issue of *Aquatic Goo Letters*.

The bad news is that if she has to run `goostats.sh` by hand using a GUI,
she'll have to select and open a file 1520 times.
If `goostats.sh` takes 30 seconds to run each file, the whole process will take more than 12 hours
of Nelle's attention.
With the shell, Nelle can instead assign her computer this mundane task while she focuses
her attention on writing her paper.

The next few lessons will explore the ways Nelle can achieve this.
More specifically,
they explain how she can use a command shell to run the `goostats.sh` program,
using loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus,
once she has put a processing pipeline together,
she will be able to use it again whenever she collects more data.

In order to achieve her task, Nelle needs to know how to:
- navigate to a file/directory
- create a file/directory
- check the length of a file
- chain commands together
- retrieve a set of files
- iterate over files
- run a shell script containing her pipeline

{% include links.md %}
