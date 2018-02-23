---
title: "Ch-Ch-Changes"
date: 2018-02-12T20:09:50-08:00
showthedate: true
featured_image: /images/vigoda-stardust.jpg
description: "Changing your shell to fish and back."
---

I hadn't gotten around to reading <a href="https://abookapart.com/products/working-the-command-line" target="_blank">Remy Sharp's command line book</a> yet, so I bought his <a href="https://terminal.training/" target="_blank">terminal training course</a> when he put it on a flash sale. One of the new things he introduced me to there was changing my terminal's shell, and though he uses zsh (and gets to that next), he starts you with something I've never seen, but that's really cool: fish.

First, let's get one thing squared away: what's a terminal and what's a shell?

## I never metaphor I didn't like

Once upon a time, a terminal was a physical device — a literal end point at which a human interacted with a machine. A synonym you'll sometimes see is TTY, short for TeleType, which was a kind of typewriter that could send input by typing commands line-by-line and receive printed output. (It's also called a teleprinter, for obvious reasons.) This is the origin of the command line interface (CLI).

Today, we mostly use graphical user interfaces (GUIs), and so we need a program to emulate the TeleType of yore. This is what we call a terminal, no longer a physical device but just another software package running on our personal computers. If you're on a Mac, the default terminal application is called Terminal, but many people prefer an alternative like iTerm2. On Linux you might use something like Gnome-Terminal or Konsole. You have choices when it comes to terminals, and you can customize their appearance and behavior.

## The shell game

The shell is a little tricky to understand only because the metaphor that produces it's name comes from its relation to the operating system and not to the user. The core of an operating system is what controls and interacts with the hardware. That core portion of the operating system is called the kernel, by analogy with the soft, chewable bit within the hard shell of a nut.

By analogy again, then, the shell should be synonymous with the physical terminal. But this is where the analogy breaks down. We don't use the shell to get to the tasty, edible bits of the nut. We strip it away and toss it in the compost. But here, with computers, we rely on the shell entirely and never actually touch the kernel.

The terminal is now the application that gets you talking to the machine — a program emulating a TeleType — and the shell is how you talk to it, a specific flavor of a command line interpreter, that facilitates your ability to send commands and receive feedback with varying levels of help and customizability. You can think of the terminal like a guitar and the shell like the strings, which can come in a variety of materials and gauges, sometimes tuned in exotic ways. One shell is a common bronze alloy, while another is nylon, and another is silk and steel. They feel and play differently, but they all make music in the same way.

## z sells z shells by the z shore

The most common shell is bash, but there are others like ksh, zsh, and others. Notice that they tend to end with sh, for shell. And we sure do love to abbreviate things when on the command line, like ch in the title of this post. But we're getting to that. Shells differ in details like whether you can group commands, how variables are set, and whether or not they support tab completion of typed commands.

Remy introduces fish, an exotic shell with tab completion, as a good starter shell, though he personally uses zsh. I'd only ever used bash, so fish was very weird and different, and the tab completion was especially cool, like working in Visual Studio with Intellisense.

But one issue I had was this: how do I get back to the land of bash?

## Ch-ch-changes

Following the fish installer, you're told to run a certain command to switch your shell, and Remy didn't go into detail here, but it's worth looking at the command:

`chsh -s /usr/local/bin/fish`

The command `chsh` means "change shell," just as `chown` allows you to change the owner of a file or directory, and `chmod` allows you to change the read, write, execute permissions for the current user, the group, and for others.

The `-s` option lets you enter that location without any additional prompting or file opening. So the command above says, "change my shell to the shell in /usr/local/bin/fish."

`chsh` actually calls the same program as two other `ch`-prefixed commands: `chfn`, or "change finger," and `chpass`, or "change password." This program allows you to change user database information, like your full name, office location, phone numbers, and, most importantly for this purpose, for the location of your preferred shell, and it doesn't matter which you use. it's just easier to remember that `chsh` is for changing the shell, and if you want to get it done without editing a file in vim, throw it up in one line with the `-s` option and the shell location.

So once you've switched to fish, if you want to change back, you just need to know the location of bash, which should be simple:

`chsh -s /bin/bash`

And from there, you can try others in the same fashion.

So that's that: a long-winded way to get around to switching back to bash from fish. I've always found it helpful to dig into what the commands actually means to understand them and retain what they do. So now I know more about it, and maybe you do, too.