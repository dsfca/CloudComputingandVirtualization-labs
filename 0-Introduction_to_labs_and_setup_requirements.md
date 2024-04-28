### [Cloud Computing and Virtualization 2023/2024](https://fenix.tecnico.ulisboa.pt/disciplinas/AVExe23/2023-2024/2-semestre) ([MEIC-A](https://fenix.tecnico.ulisboa.pt/cursos/meic-a)/[MEIC-T](https://fenix.tecnico.ulisboa.pt/meic-t), [METI](https://fenix.tecnico.ulisboa.pt/merc), [MECD](https://fenix.tecnico.ulisboa.pt/cursos/mecd))
&nbsp;
&nbsp;
&nbsp;
&nbsp;
<!--
- Week 2 (May 8-12th)
    - [Introduction to AWS - Amazon Web Services](labs/lab-aws/README.md);
- Week 3 (May 15-19th)
    - [Introduction to Javassist - Java Bytecode Instrumentation Tool](labs/lab-javassist/README.md);
- Week 4 (May 22th-26th)
    - Project support;
- Week 5 (May 29th-June 2nd)
    - [Introduction to Function-as-a-Service](labs/lab-faas/README.md);
   - Paper presentations;
    - Checkpoint evaluation and feedback;
-->
## Introduction to Git
Make sure that you are familiar with the following concepts: `commit`, `push`, `pull`, `clone`, `fork`. Tutorials:
- [gittutorial](https://git-scm.com/docs/gittutorial)
- [git - the simple guide](https://rogerdudler.github.io/git-guide/)
---------------------------------------------------------------------
Git commands:
<code>
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
</code>
<code>git config --global user.name "Mona Lisa"</code> (set a git username - for every repository)
<code>git config --global user.email "@"</code>
<code>git config user.name "Mona Lisa"</code> (set a git username - for single repository - Change the current working directory to the local repository where you want to configure the name that is associated with your Git commits.) 
<code>git config user.name</code> (check)

## CNV Linux Environment
We provide a light and optimized VM with all the software necessary to run CNV labs and project. This VM is based on Vagrant and VirtualBox.

CNV requires a Linux development environment. We strongly recommend using the VM we provide. However, if that is not an option for you, there are several other alternatives:
- use lab computers (even if through remote connection, i.e., SSH);
- build your own Linux Virtual Machine;
- use the [Linux Subsystem](https://docs.microsoft.com/en-us/windows/wsl/install) (Windows users);
- install the software manually (for Linux and Mac users).

## Tutorial
## Overview

It will setup an optimized (smaller, hence faster) virtual machine bundled with only the tools required for the CNV course.

---

## Preliminary Set Up of the Host Environment

This section describes the minimum setup of the CNV virtualized environment. We will use the following tools or programs: 
- **Vagrant**: is an open-source product for building and maintaining portable virtual development environments.
- **VirtualBox**: Oracle VM VirtualBox is a free and open-source hosted hypervisor for x86 virtualization.

### Installation For Windows 10 systems

For Virtualbox, go to the [Downloads page](https://www.virtualbox.org/wiki/Downloads) and select the Windows hosts latest binaries. If you wish to use VirtualBox on Windows, you must ensure that Hyper-V is not enabled.

For Vagrant, go to the [Downloads page](https://www.vagrantup.com/downloads) and select the WINDOWS installer of the latest version of Vagrant for your system.

## Creating and using the Virtual Machine for the Lab

Having the host environment prepared, it is now time to create the VM! If you have ever tried to create Virtual Machines used for testing through a Graphical User Interface (GUI), you know that it can be a painful and very manual process (installing the Operating System, the packages/applications, configure them, etc.) or downloading an already created VM with several GB of size that takes a huge amount of time to download. There is also a tendency to leave forgotten VMs around in your computer (when running, consuming precious resources, when shutdown still using up space) for a long time.

Vagrant eliminates much of that extra labour, as most of the process is completely automated.

To get started you need to position the creation of the VM in an adequate working folder. It is recommended that the work directory (folder) does not have a name with spaces and/or accented characters, and that specifically in Windows, not placed under the user's HOME folder. Therefore, use, for example:
- in Windows `D:\cnv\`
- in macOS or Linux `/cnv/`

There download the following files: [cnv-provision.sh](cnv-provision.sh), and [Vagrantfile](Vagrantfile) which will allow a smooth setup of the system.

`vagrant up` - start/power up the VM in Terminal (or Powershell) inside the working folder

The first time you start the VM it will in fact build it, and so it may take up a few minutes, depending on the speed of the host system and of your Internet connection. When finished the VM is booted.

`vagrant ssh` - establish sessions with the VM using the following command (secure shell, without needing username or password)

For convenience, you can issue this command in as many shell/windows/sessions as you want so that you can have multiple windows logged to your VM. The session is established and you will get the machine prompt similar to the following:

<pre><code>
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-136-generic x86_64)
 
vagrant@cnvlab:~$
</pre></code>

When you have finished your work, and in order to exit the session with the VM use the command `exit`:

<pre><code>
vagrant@cnvlab:~$ exit
logout
Connection to 127.0.0.1 closed.
</pre></code>

`vagrant halt` - to stop the Virtual Machine (the first is equivalent to a shutdown)

`vagrant global-status` - to verify the global state of all active VM environments (managed by Vagrant) on the system.

The last command allows you to confirm that the statuses of the VMs is powered off. The next time you want to work with the VM again, then use the command (the VM will boot in less than a minute, typically):

`vagrant up`

### Shared Folders with the VM

The VM is prepared to have a shared folder structure with your host system. You will notice that when creating the VM for the first time, that a new folder with the name `cnv-shared` appeared in the working directory. That folder is also accessible inside the VM, and so, whatever you place in that folder is accessible from both your host machine and the VM.

With this feature, you will be able, for example, to edit your Code using your preferred Code Editor (e.g., VScode, Eclipse, Atom, etc.), and then, inside the VM just use/compile/run the code.
