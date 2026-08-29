# Rank 01 · Born2beroot

## Objective

Configure and explain a hardened Linux virtual machine rather than simply installing an operating system.

## What it teaches

Users and groups, least privilege, SSH, sudo policy, password aging, partitions, firewall rules, package updates, monitoring, and operational documentation.

## Workflow

`create disposable VM → partition → create users/groups → configure SSH/sudo → apply firewall → add monitoring → verify → document`. Every security choice should have a command that proves it is active.

## Usage and evaluation tips

Work only inside a disposable VM. Keep a console open while changing SSH. Demonstrate firewall status, password policy, sudo restrictions, disk layout, hostname, and the monitoring script. Explain why each control reduces risk.

## Common mistakes and improvements

Weak passwords, excessive sudo rights, an SSH lockout, undocumented changes, and testing on production are the main hazards. Improve with a reproducible setup checklist and a recovery plan.

## What I learned

Secure, observable infrastructure is part of professional software engineering.

See the [animated lesson](../../../lessons/index.html#born2beroot).
