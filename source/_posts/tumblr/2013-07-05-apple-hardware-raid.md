---
layout: post
title: Apple Hardware RAID
tags:
- apple
- RAID
- technical support
- hardware
- recovery
- rebuild
- failure
---
When I got home yesterday, I noticed that our 2009 Mac Pro was unresponsive. I
checked to see if it was on the network, and then powered it down. When I
turned it back on, it booted into the recovery volume.

That Mac Pro had a RAID 5 array on it, composed of four 2TB hard drives,
bought for a premium price from Apple so they would support the system.

I opened up the RAID utility and saw that the RAID controller was recognising
all four hard drives were no longer in a RAID set. Although all of them were
reporting that they were "ok", the RAID set and therefore the RAID volume were
gone.

I telephoned Apple, happy to pay for someone to guide me through the recovery
since there is **absolutely no** documentation on recovering a RAID 5 system
with a missing RAID set. Their technical support was courteous, but not well-
informed.

After going over it and leaving it with them to "investigate" further, I
received a phone call today from the person who was helping me. The short of
it is that Apple say if your RAID set is missing, you're screwed. They also
say that you should not be using RAID for backup purposes, as it's only
designed to protect you from disk failure.

But of course it wasn't a disk that failed. It was the RAID itself, and it
took out all our data with it. We will be restoring from backup, but the size
of the RAID (4.7TB) meant that backing up to external drives is complicated,
and our backups are not completely up-to-date.

The point is that we paid nearly £500 for the RAID card and it has proved to
be a complete waste of money. If your Dell RAID dies on you, then Dell will
help you recover it, but clearly Apple don't take their business support
seriously.
