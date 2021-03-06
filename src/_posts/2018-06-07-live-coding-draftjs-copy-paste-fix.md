---
layout: post
title: Live coding – Draft.js copy-paste fix
date: 2018-06-07 18:21:47 +0300
comments: true
categories: [Draftjs, Draftail, Streaming]
canonical: https://www.draftail.org/blog/2018/06/07/live-coding-draftjs-copy-paste-fix
---

Most of the functionality of Draftail comes from Draft.js, and so do the bugs. One of the most problematic ones for us was the poor support for [copy-paste of content between editors](https://github.com/facebook/draft-js/issues/787). Here’s me live coding my attempt at a fix.

<!-- more -->

## Take one

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/TVhFDnJAOYk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

PR: [thibaudcolas/draftjs-conductor#2](https://github.com/thibaudcolas/draftjs-conductor/pull/2)

## Take two

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ExL5k0HppIg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

PR: [thibaudcolas/draftjs-conductor#3](https://github.com/thibaudcolas/draftjs-conductor/pull/3)

---

This is now available as a PR to Draft.js, and as a separate package ([`draftjs-conductor`](https://github.com/thibaudcolas/draftjs-conductor)), over at [facebook/draft-js#1784](https://github.com/facebook/draft-js/pull/1784).
