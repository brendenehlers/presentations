---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Else Statements
info: |
  ## Why you shouldn't use else statements
  When programming, the use of else statements is typically a sign that the code needs to be refactored. In this presentation I'll explain why

  Based on my [blog post](https://dev.to/behlers/you-shouldnt-use-else-statements-33h7)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Why you shouldn't use else statements

most of the time.

<!-- Who Am I? page -->
---
layout: intro
---
# Who am I?

- Full stack developer with an backend focus
- Blogger

---
---

# What do I have against `else` statements?

Else statements are a symptom of bad code.

<!-- Messy example -->
---
src: pages/messy-example.md
---

---
layout: quote
---

# Guard Clauses

Guard clauses are checks on variables that will end the function execution when the check fails.


<!-- Guard clause example -->
---
src: pages/guard-example.md
---

---
---
# Some cool advantages

- Contract
- Cleaner diffs
- Core logic is easy to find

---
---
# Exceptions

As with anything in software engineering, there's exceptions to the rules

---
---
# Shameless Plug

I wrote a blog post on this topic, check it out if you're interested.

<!-- Add QR code to the post -->

dev.to/behlers

---
layout: end
---
# Thanks!

Any questions?