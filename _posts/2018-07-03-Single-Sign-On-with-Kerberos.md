---
layout: post
title: "Single Sign On with Kerberos"
date: 2018-07-03
---
## Automatically get your Kerberos Ticket
Using a Linux desktop as your daily driver for work can sometimes be a challenge.  Windows users get all sorts of helpful configurations applied to their machines by default because they are "joined" to the domain.
 
When logging into any Windows machine on the domain you use your Active Directory credentials and are automatically presented with a kerberos ticket, your network shares are already mounted, and your browsers are already configured to use Single Sign on. 

In Linux we can work around this with some post login processes via scripts or just remembering to manually `kinit` every morning.

Better yet, let's do it automatically. 
 
### no need to kinit every morning
### Prep work
* `sudo apt install -y krb5-user libpam-krb5`
* Set your default realm when prompted, or modify /etc/krb5.conf
  * default realm = DOMAIN.EDU
* Modify your local user account to have the same name and password as your Active Directory account
 
### Configure pam and kerberos
`sudo vi /etc/pam.d/common-auth`
```bash
auth    required                        pam_unix.so
auth    optional                        pam_krb5.so use_first_pass
```
### Change Google Chrome launch options
`sudo vi /usr/share/applications/google-chrome.desktop`

Find this line:
 
 `Exec=/usr/bin/google-chrome-stable %U`

Add the whitelist flag:

  `Exec=/usr/bin/google-chrome-stable %U --auth-server-whitelist="*domain.edu"`
