---
title: "Using the Wordnik API"
date: 2018-02-20T11:38:30-08:00
showthedate: true
featured_image: /images/stegosaurus-def.png
description: "Creating a shell function to get quick dictionary definitions on the command line, because, why not?"
---

One thing I've finally learned is that whether you're running bash or zsh in your terminal, the file where you customize your instance ends with `rc`, which stands for "runcom," or "run commands," dating way back to 1965 in the early days of UNIX. `.bashrc` is the file that contains commands to be run when the bourne again shell (bash) starts up, and `.zshrc` has the commands to be run when the z shell (zsh) starts up. And you'll find it elsewhere, for example in `.vimrc`  if you're into Vim.

One of the really cool things you can do here is reference environment variables, aliases, and functions stored in external files. So I wrote the following function using the <a href="http://developer.wordnik.com/" target="_blank">Wordnik API</a> so I can quickly define words on the command line.

<script src="https://gist.github.com/denmch/f7d9b8e0f01b2ab67ec633ccc9799f9f.js"></script>

If you don't know <a href="http://wordnik.com/" target="_blank">Wordnik</a>, you should check it out. It's a great site, and when my confirmation email didn't come through Erin McKean quickly responded herself and activated my account, which felt pretty cool.

The function works like a shell command and can take an argument, which is represented within the function as `$@`. This grabs any and all positional parameters, e.g., if the command takes three parameters, they'd be referenced as `$1`, `$2`, `$3`. So `$@` just takes one after the other and passes them all in. The local variables `array` and `string` it into a string and then replace the spaces between parameters with `%20` so that the result works within the url in `curl`.

The `curl` command is one of those that you find all over the web in places like StackOverflow, where people say, "Just type curl blah bitty blah blah." It's just one of those things that you use to do something. But as often happens, it turns out to be helpful to know what the name means, so that you can retain the meaning. In this case, its name is styled cURL, like the ubiquitous acronym URL. It's written in C and though originally meant to be pronounced "see URL," it was later treated as a backronym for "cURL URL Request Library," as the creator described on cURL's 17th birthday. (As of this writing cURL is nearing 20!)

Knowing that history we remember either that cURL allows us to "see" stuff at a given URL, or that it's a library written in C used to request information from and about URLs.

We run `curl` with a `--silent` option. If you were typing this a lot on the command line, it'd be faster to use `-s`, but for the purposes of a readable gist, it seems beneficial to type out the option, explaining clearly that we want our `curl` output to be silent, i.e., to not show us the progress bar, etc. To get a result, you need to add your Wordnik API key (I've added mine as an environment variable sourced in my `.zshrc` file).

We pipe the output through `json` with the `--array` option (aka `-a`), and the lookup parameter `text`, which is the key that should grab each definition in the JSON results from Wordnik.

These results are then piped to `cat` with the `-b` option, which numbers non-blank lines in returned results. I'm not sure the `-b` options is necessary given the results (`-n` could be sufficient), but it doesn't hurt.

So just for fun, here's the result, with the added bonus of piping the output to `cowsay -f stegosaurus` (where the `-f` option is short for "file", i.e., which "cowfile" is used for the ASCII art).

`def learning | cowsay -f stegosaurus`

<img src="/images/stegosaurus-def.png" alt="An screenshot of a terminal window showing ASCII art of a stegosaurus speaking three definitions of the word learning." />