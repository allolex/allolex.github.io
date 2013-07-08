---
layout: post
title: Restricting users when setting up a file transfer server
categories:
- OpenSSH
- SFTP
- System Administration
- chroot jail
- Unix
- Linux
---
[Restricting users when setting up a file transfer
server](http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-
chrooted-ssh-sftp-debian-squeeze)

In my role of Production Manager at Southern, I keep running across rather,
shall we say "sub-optimal" server configurations for delivering masters,
artwork and other very large files to manufacturers.

For example, one of the plants we have worked with has a single SFTP account
for all their clients to upload their masters to. It's not an append-only
solution like an OS X "Drop Box" where people can't see what was uploaded--you
can potentially download other companies' masters. Another company we work
with for digital retail doesn't let you read anything, but you can see all of
their clients. There aren't many servers I think have been set up well.

I've decided that it's a basic system administration skill to be able to set
up private, chrooted SFTP accounts for any number of users on a system, so I'm
linking to this HOWTO, which worked very well for me. Just create a user and
home directory, add it to the "transfer" group, create a subdirectory under
the home and chmod it so it's world readable/writable/whatever.

A couple of important notes about the configuration:

  * Make sure you put the "Match" stanza at the very end of the ssd_config file. I had a single directive after it, which sshd parsed as if it were part of the stanza. Not good.
  * Even though the entire path has to belong to and be writable only by root, you can still use the %h variable to chroot individual user directories, and then put useful directories underneath the home, for instance "pick_up" and "drop_off" or similar.

Here's the bottom (and relevant) part of my sshd_config:

{% highlight python %}
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp  
UsePAM yes  # not relevant to this discussion, but see my point 
            # above about Match being at the *bottom*
Match Group transfer 	
  ChrootDirectory %h 	
  AllowTCPForwarding no 	
  X11Forwarding no 	
  ForceCommand internal-sftp
{% endhighlight %}

[Read the HOWTO](http://www.howtoforge.com/restricting-users-to-sftp-plus-
setting-up-chrooted-ssh-sftp-debian-squeeze).
