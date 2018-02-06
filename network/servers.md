<title>network - servers</title>

# Network - Servers

Linux server distributions are meek operating systems, just running and doing exactly what you want them to do. They are configurable down to the Kernel. You can update them from a single source and they do not need a reboot most of the time - even then you have all the freedom to decide when to reboot the machine.
Since you can customize them to an extreme extend, Linux is easy to secure against attacks (but it's also easy to get the config wrong)

Linux is very resource friendly and you can remove everything you don't need (or not even install it in the first place. No one needs a desktop on a server. Servers are "headless" most of the time. It runs on the smallest VMs. I've seen <1€/month Linux servers which are ideal for your personal site and applications.

Many file systems are only available for \*NIX, for example the brilliant ZFS. Most of the time, NTFS is not enough for enterprise servers, when you want special things, like snapshots, distributed computing,...
I've seen webservers having sever problems with Windows services (for example there was a version of MariaDB which would kill the system log process because it used an "unknown" event ID. The Microsoft support blamed MariaDB instead of working on a bugfix which would prevent the whole service from crashing just because of an unknown integer value in the first place)
As for macOS and Windows:

macOS is not a server OS. Apple once tried to make a server OS, but they failed and afaik abandoned the project. Desktop OSs are missing many administrator options which are important to set up specialized software and custom behaviours.
Actually Windows Server is a very nice server system for people who can't use the commandline. There are quite a lot of people who need a GUI or they cannot use the system at all, so enterprises use Windows servers in favor of *NIX (where I work we have less than 10% *NIX systems and I had to decide against RHEL because of my coworkers). Windows has one big disadvantage: It costs quite a sum, so people who can use the commandline and know Linux will prefer the free Linux option (why pay for it when I can have it for free :) )

## Why do most run on Linux?

Linux is free. Not just free as in beer, but free as in speech. This meant that you could install Linux on any machine and not have to worry about paying for it or obtaining licences.
Most software for Linux is free! So not only can you get a server running on a free OS, you can then proceed to fill it full of free and useful software.
Apache.

Apache might be one of the more important reasons for the dominance of Linux in the server market. When the web was just reaching the elbow of it's exponential growth, the apache server was released. This was enterprise-grade server software available for free. It might not have been the absolute best server package out there, but it was free.
Security.

The Linux source code can be independently audited, and if new exploits appear, the entire community can response to fix the issues. This is much better in my opinion than hoping that a company like Apple/MSFT find possible vulnerabilities in their own code and fix them before the bad-guys can find them. The sheer scale of the amount of people relying on and contributing to Linux helps to make it more safe.

## Virtual Private Server (VPS)

Shared server, so you geta little chunk of a server, but they're _virtualized_ so that little chunkc acts as your own independent server, so you can configure it how you want.

Essentially a blank slate.

## Shared Server

i.e. Dreamhost, GoDaddy

You get a little chunk, but you don't have control of the software being run there. Everything is preconfigured
