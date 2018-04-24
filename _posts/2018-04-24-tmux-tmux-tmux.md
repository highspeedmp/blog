---
layout: post
title: "tmux tmux tmux"
date: 2018-04-23
---

## tmux

One way to describe it is tabs for your terminal.  Or [GNU Screen][gnu-screen], but different.  I first made the switch from screen to tmux because tmux by default has a tab bar.  Simple, I know, and you can do that with screen too. Making the switch encouraged me to explore my configuration more.  With screen I was just using it to keep a session alive for long running jobs, nothing more.  With tmux I wanted to lay out my workflow and make my life easier. 

Here you can see I have 2 seperate panes open working on 2 different files.  Along the bottom is the tag index and the time and date. 

![tmux screenshot]({{ "/assets/tmux.png" | absolute_url }})

tmux is awesome. You can see that I'm using it right now. I keep a session open all the time laptop, my raspberry pi is running a session or 2, and I have many sessions open on the server where I do my work. 

### Installing tmux

_Easy_
```
apt -y install tmux
```
This will install tmux on your system, replace apt with yum or pacman or brew to get it from your package manager. 

However, this does not install the latest and greatest version of tmux. Version 2.6 and later versions have a really cool session manager that displays previews of all your open panes and windows.

To do that, you'll have to build it from source. I found this [gist by P7h][tmux-gist]. 

{% gist 9ea946f94afc778a95926a6b87a4fd34 %}

### Configure tmux

tmux will load a configuration file from your home directory ~/.tmux.conf

I've borrowed many different configurations from other people along the way, and this is what I have come up with.  I've set the prefix key to \` which makes for easy to type key combos. I attempted to comment as much of the configuration as I could along the way, but not all of it is commented.  

{% gist 836a2680c58c02ec1e36eff11aa96666 %}

[gnu-screen]: https://www.gnu.org/software/screen/
[tmux-gist]:https://gist.github.com/P7h/91e14096374075f5316e
