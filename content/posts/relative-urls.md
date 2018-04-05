---
title: "Relative URLs Desmystified"
date: 2018-04-01T20:06:21-07:00
showthedate: true
description: "Explaining the meaning of slashes and dots in various combinations"
---

The first key to really understanding relative URLs is to recognize that they refer to the current URL and do not reflect the actual folder structure on disk. The notation used is analogous to file navigation, but in this context you're not traversing the physical structure: the browser constructs the new URL from the current URL value using a simple but surprisingly robust set of symbolic notation.

Let's take a look at a handy table, and then I'll dig in. There are exactly four distinct symbols with very precise meanings:

Symbol   | Meaning      | Notes
-------- | ------------ | ---------------
`/`      | Root         | up to base URL
`//`     | Protocol     | to be avoided
`./`     | Current dir. | alias: no slash
`../`    | Parent       | may be combined

These symbols are composed of just slashes and dots, singly or in pairs. It may seem confusing at first, but the first three are constant and can not be combined. The last one, with two dots, can be combined, as we'll see below.

## 2 Slash or Not 2 Slash?

The simplest way to conceptualize the double slash and the single slash in relative URL notation is to recognize that the base URL is the kernel, and to think of the double slash and single slash as something like bookends. One separates the base URL from its protocol, and the other separates it from its subpages and directories:

Protocol | delimiter | base url | delimiter | subpages, &c.
-------- | --------- | -------- | --------- | -------------
https:   | //        | dev.to   | /         | denmch

The double slash will tell the browser to build a URL from just before the base URL, going back to the protocol. The single slash by itself tells the browser to construct a URL from just after the base URL, at the level of subpages and directories.

Given the URL `https://dev.to/denmch`, double slash (`//`) is shorthand for `https://` and single slash (`/`) is shorthand for `https://dev.to/`, quite literally telling the browser to begin at this or that distinct delimiter.

## Protocol Considered Harmful

You've doubtless linked to or at least seen external resources without a stated protocol (`http:` or `https:`), using a url of the form `//path-to.my/script.js`.

This seemed just dandy for awhile, but it's now [considered an anti-pattern and potentially exposes vulnerabilities](https://www.paulirish.com/2010/the-protocol-relative-url/). Even though it's probably best avoided, it's good to know why it works the way it does, and it helps us to gain a deeper understanding of how relative URL notation really works, especially since it's still found out there in the wild (even if we should avoid it).

## Dot Dot's my father's name; call me Dot

Whereas slashes by themselves refer to the bookends around the **base URL**, *single slashes in combination with dots* refer to the full **current URL** and move from right to left.

Dot qualifiers tell the browser that *this* slash is *not* root. Semantically, a single dot followed by a slash (`./`) means "start from the current directory." The `./` symbol will never be found in any other combination (e.g., `.././` would be invalid).

A double dot followed by a slash means "start one directory up," and this pattern can be compounded to traverse leftward in the current URL, so that `../` references the parent of the current directory and `../../` references the parent of the parent, and so on.

If the relative URL references more "generations" than the current URL contains, the new resulting URL will start only as far back as it can: at the base URL:

Given the URL `https://dev.to/denmch`, the following patterns all go back to the base URL (`https://dev.to`) because there are no parent directories to extrapolate from the current URL:

- `../../../`
- `../../`
- `../`

The last important bit is to recognize that `./` has an alias: beginning a relative URL with neither dots nor slashes. Given the current URL `https://dev.to/`, a relative url of the form `href="denmch"` would be functionally equivalent to `href="./denmch"` and result in a final URL of `https://dev.to/denmch`.

Now it's up to you do decide when and where it makes sense to use relative URLs, and hopefully you're better equipped to think it through and understand problems and potential problems as they arise.