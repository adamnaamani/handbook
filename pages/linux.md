# Linux

Linux is a family of open source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds.

## Table of Contents
1. [/etc](#etc)
1. [crontab](#crontab)

## /etc
ETC is a folder which contain all your system configuration files in it.

> “etc” is an English word which means etcetera i.e in layman words it is “and so on”.

## crontab
Files used to schedule the execution of programs.

> A crontab file contains instructions for the cron daemon in the following simplified manner: _"run this command at this time on this date"_. Each user can define their own crontab. Commands defined in any given crontab are executed under the user who owns that particular crontab.

```bash
cd /etc
nano crontab

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the 'crontab' command to install the new version when you edit this file and files in /etc/cron.d. These files also have username fields, that none of the other crontabs do.
```
