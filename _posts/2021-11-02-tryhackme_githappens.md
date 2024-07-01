---
title: Tryhackme - Git Happens
date: '2021-11-02 22:30:00'
description: Boss wanted me to create a prototype, so here it is! We even used something called "version control" that made deploying this really easy!
categories: [TryHackMe, 'Git Happens']
tags: [tryhackme, 'git happens', git]
---

# Git Happens

TryHackMe Room Link: [Git Happens](https://tryhackme.com/room/githappens)

## Task 1 Capture the flag

Find the Super Secret Password

---

## Walkthrough
We begin this challenge room by running a nmap scan to see what ports are open.

  ![](/assets/img/tryhackme_githappens/01-nmap.png)
  
From the nmap scan we can see 1 port open.  
Port 80 http  

The nmap scan also informs us that there is a `.git` directory on the website.
  
  
  Checking the website only shows a login screen
  ![](/assets/img/tryhackme_githappens/02-home_page.png)
  
  When we test logging in with  username `admin` and password `admin`  nothing appears to happen.  
  There is no error message.
  
  The nmap scan lists a `.git` directory lets check that now.
  
  ![](/assets/img/tryhackme_githappens/03-dot_git.png)
  
  We can see the folder structure of a git repository.  
  We can check each folder and file individually but it is better to download the git repo and check it locally with git.
  
  To download the `.git` directory we can use [GitTools](https://github.com/internetwache/GitTools).  
  Lets clone the GitTools repository to our local machine
 ![](/assets/img/tryhackme_githappens/04-clone_gittools.png)
 
 Now that we have the tools we can download the `.git` directory.  
 
 ![](/assets/img/tryhackme_githappens/05-gitdump.png)
 
 Now we can go into the newly created git folder and see what commits were made on this repository.
 ![](/assets/img/tryhackme_githappens/06-git_log.png)
  
  Looking at the messages for the commits we can see that the site was made more secure with each commit applied. 
  So we want to be looking at the early commits before any security was applied.
  
  We need to find a password so checking commits before any security was implemented is the best option.  
  There are 2 commits availables  
  - Made the lgin page, boss!
  - inital commit
  
  We use the checkout command to revert the repository back to an earlier commit.
  
  ![](/assets/img/tryhackme_githappens/07-git_checkout.png)
  
Once the checkout is completed we now have 2 files and 1 directory.  
Let's check what is in `index.html`.  
Scrolling through the html file we can see a `login()` at the end of the file and it contains the username and password in plaintext.

![](/assets/img/tryhackme_githappens/08-index_password.png)

Entering the password on tryhackme will complete the room.
