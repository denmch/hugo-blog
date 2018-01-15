---
title: "Class Struggle in the 21st Century"
date: 2015-12-29T16:12:07-08:00
showthedate: true
featured_image: /images/class-class-class-bw.jpg
---


<p>Not that kind of class struggle. I’m talking CSS classes, which — Whoa! What was that?! Wait a minute. Important message incoming.</p>
<blockquote>You need a second level heading, text in red, in 60 seconds or this bus will explode. What do you do, hotshot? WHAT DO YOU DO?</blockquote>
<p>Welp, it’s go time! So, if you’ve followed a Web tutorial or a popular framework I guess you go ahead and create a class called <strong>.red-text</strong>. And … done.</p>
<figure>
    <img src="/images/speed.jpg">
    <figcaption>What do you do?! You write a new class that tells you exactly what it does! Credit: Speed</figcaption>
</figure>
<p>Boy, that was fast. Why does Keanu make it look like so much work?</p>
<p>It’s such a great idea, too, because anyone looking at the HTML knows what the visual style will be! Because those are two layers we definitely don’t want to separate. We have a style sheet for some other reason, I think.</p>
<p>Well, as the project grows and the site ages the memos keep coming in that more and more bits of text need to be red. Maybe everyone is convinced users won’t notice the <em>really</em> important stuff (i.e., the stuff they own) without it. And so you throw that class everywhere like tinsel on a bare Christmas tree.</p>
<blockquote>&lt;p class=“red-text”&gt;, &lt;span class=“red-text”&gt;, &lt;div class=“red-text”&gt;, <em>&lt;li class=“red-text”&gt;, und so weiter.</em>
</blockquote>
<p>So easy. So efficient. But you know what, Peter? We’re going to have to go ahead and ask you to change all of the red text to blue text. Yeah … we’re rebranding and market research says the kids feel really safe with blue, so … ‘k. Thanks!</p>
<figure>
    <img src="/images/lumberg.jpg">
    <figcaption>If you could just — add a color thingy — that’d be great. Aaaand put it everywhere. Yeah. Credit: Office Space</figcaption>
</figure>
<p>No problem.</p>
<blockquote>.red-text {<br> color: blue;<br>}</blockquote>
<p>Oh. Hm. Well, let’s change <em>.red-text</em> to <em>.blue-text</em>. Wait — all of the text is blue now, but <em>says</em> it’s red. Oh, snap! I have to go into every document on the site and change the class assignment <strong>“red-text”</strong> to <strong>“blue-text”</strong>. But I’m clever. I’m computer savvy. I can do a quick search and replace and fix all … whoa … 9,347 instances of ‘red’. Well, here goes … and … BOOM!</p>
<p>Now we’re talking. The text is blue all over the place. The site makes me feel safe and cozy. They were right about that market research. People can still view source and see that, yep, the blue text sure is labeled <strong>“blue-text”</strong>. All is right with the world.</p>
<figure>

<img src="/images/hackerman.jpg">

<figcaption>Not so fast, Hackerman! Credit: Kung Fury</figcaption></figure><p>But suddenly you hear hurried footsteps across the floor, and the boss is back.</p>
<blockquote>Peter, <em>Stephanie Redner’s assistant just called </em>in from the home office. They want to know why the site says “<em>Stephanie Bluener (pictublue here) usheblue in a new era.”</em> This isn’t good, Peter. This isn’t good at all.</blockquote>
<p>Silly example? Maybe. But it’s happened. Maybe not exactly that way, but it’s happened. But it’s not even that scenario that’s really the problem. It’s that when you name your classes in this way, you — <em>almost</em> — may as well be writing inline styles.</p>
<figure>
    <img src="/images/engineering.jpg">
    <figcaption>Credit: <a href="http://www.bonkersworld.net/building-software/" target="_blank">http://www.bonkersworld.net/building-software/</a></figcaption>
</figure>
<p>This happens naturally as a consequence of unintentional design. The site looks and functions a given way because it was tinkered with, piecemeal. And refactoring is hard to do in the real world when the culture doesn’t value it.</p>
<p>You’re short on time. The people with the money don’t get why it’s important — or that it can be problematic in the first place. And really, when your kid smashes a hole through the drywall, you patch it up. You don’t tear down the wall and build it up again. It’s also a super fast fix when someone over your head has notes on an existing site.</p>
<p>So I get it. But it’s kind of become the default. And that’s not a good thing.</p>
<p>Here’s a related issue: you’re using a framework and want buttons to look and act like buttons. It’s not enough to add a <strong>&lt;button&gt;</strong>: you have to load it up like a baked potato:</p>
<blockquote>&lt;button class=“btn btn-default”&gt;</blockquote>
<p>So what might you do differently?</p>
<p>In the last example, maybe <strong>&lt;button&gt; </strong>should be enough for the default. Do we really need to say that button is part of the class of buttons, and should we ever need to declare a default?</p>
<p>In our hypothetical business, maybe it turns out that when you look more closely the <strong>&lt;h2&gt;</strong> is only red when it falls within a div in the <strong>.widget</strong> class. Maybe <strong>&lt;p&gt;</strong> is only red in those financial terms divs that accounting made you add, the one with that dumb <strong>.notice</strong> class (so garish, but they insisted). And so on.</p>
<p>Well, here’s a better way: leave your HTML uncluttered, and get to know your CSS selectors. We don’t even need to get fancy (yet). We can use a simple descendent selector, which you may know better as a space.</p>
<blockquote>.widget h2, .notice p {<br> color: red;<br>}</blockquote>
<p>This is what I dreamed about almost 20 years ago when I was making websites for myself and getting so excited about the future of CSS. It’s kind of heartbreaking hving come back into the field only to find that CSS is blamed for the baffling prevalence of a bad practice.</p>
<figure>
    <img src="/images/b2tf.jpg">
    <figcaption>Great Scott, Marty! Has the state of CSS gotten that bad in the future? Credit: Back to the Future</figcaption>
</figure>
<p>Littering your HTML elements with classes — especially overly declarative classes—creates maintenance nightmares, produces cluttered markup, and kind of defeats the purpose of separating semantics and style.</p>
<p>So if you can, just don’t ever get on that bus. But if you do, try to mitigate things where you can. And in the end, remember what you’re trying to do in each document, and don’t duplicate your efforts.</p>

