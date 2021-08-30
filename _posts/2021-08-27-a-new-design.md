---
title: A New Design
author: Me
layout: post
date: 2021-08-27
---

Hi, I redesigned my site a few weeks ago. I'm only writing about it now, because I just added a pretty big thing: iA Writer Mono.

**The Font**

I didn't like how Courier looked after a while, so I wanted a cleaner and prettier monospace font. I started with JetBrains Mono, but something didn't sit right for me. Then I experimented with San Francisco Mono, the font used in Xcode, and decided against it for fear the wrath of Apple's legal team. I then was reminded of [iA Writer's custom-made fonts](https://github.com/iaolo/iA-Fonts) that the wonderful folks at iA are letting anyone use.

So I snagged them, loaded the Mono variant into my CSS, and it looks beautiful. I love it. OK, font and all, I need to talk about this new design.

**The Design**

My old design was getting stale and convoluted. I wanted to keep the aesthetic of the old design, in a way, but wanted a nice refresh that presented only the information needed in a nice way. A few years ago, I designed my resume with a monospaced font, double-column layout, and a concise way to see my experience on one page. So I took inspiration from that, and out came this design.

I kept the same color scheme as the old design: light text on a dark background with blue link highlights that turn red on hover. I muted the colors a bit, which made them easier on the eyes and gives it a sort of retro vibe. (Fun fact, I was actually inspired by the Metal Gear Solid 3 UI color scheme in a way.)

My name is on its own line, on the left column, justified right. It immediately brings your attention to the fact that this is, indeed, my site. Below that is the same About blurb from the old design. Below that is my contact info, followed by a design and font credit. For the list of my projects, I used the format from my resume: Title, Link, Blurb. One sentence for the blurb, and the most concise title possible.

My apps are split into the same sections as on the old design, but I split the Miscellaneous page into a few different sections and kept a true Miscellaneous section at the very bottom.

The differentiation for each level of importance took a while to figure out. The main titles are standard **h1** and **h2**s, the project titles are just bold **p**s, links are italicized **p**s, and the descriptions are standard **p**s. However, the more lengthy text such as the project descriptions and About section are slightly darker than the primary color. This helps draw your eye to the section markers instead of the long text, making the layout look less cluttered.

I also whipped up a quick favicon. It's my initials in iA Writer Mono on a squircle with the same text and background colors as the site. It helps complete the look and makes the design appear finished.

**The Blog**

There isn't too much here. In the recent posts page, I turn the projects list into the posts list. Clicking my name also brings you back to the main site. In the archive, the right column turns into a posts list organized by year and month, same as before. The left column is navigation.

**The Mobile Layout**

I never really used proportional text sizes before, so adapting this layout to work on mobile was a little tricky to get working. I found a good proportion of the viewport width to use for the text size, adjusted a few margins and stuff, and adapted the layout's flexbox to be vertical instead of horizontal.

On the main site, having the About section and contact info on the bottom seems most logical. On the blog, I keep the navigation on the top and wrap the options if the screen is too thin. I think that's a good compromise for a functional mobile layout, done only in pure CSS.

**In Conclusion**

I'm super happy with how this redesign came out. I've wanted to do something like this for a while, and I'm so glad I went through with it. It's more concise, clean, and pretty. And most importantly, there's still no JavaScript to weigh the site down. Thanks to everyone in the [Relay FM Members' Discord Server](https://www.relay.fm/membership) who gave feedback and suggestions for the layout.

 Enjoy.
