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

# Why you shouldn't use else statements...

<v-click>...most of the time.</v-click>

<!-- Who Am I? page -->
---
layout: intro
---
# Who am I?

- Full stack developer
- Open source enthusiast

<!-- Messy example -->
---
src: pages/messy-example.md
---

---
layout: fact
---

# Guard Clauses

<p>Guard clauses are checks on variables that will end the function execution when the check fails.</p>


<!-- Guard clause example -->
---
src: pages/guard-example.md
---

---
layout: section
---
# I'm not convinced

<v-click>
  <p>Let's talk about the advantages</p>
</v-click>

---
---

# Functions are easier to understand
<div grid="~ cols-2 gap-2" m="t-2">
<p>Old Code</p>

<p>New Code</p>

```ts {all|5|all}
function createUser(db: Database, user: User) {
  if (user != null) {
    if (db.isConnected()) {
      if (!db.hasEntry(user.email)) {
        return db.create(user)
      } else {
        throw new Error("user already exists")
      }
    } else {
      throw new Error("database not connected")
    }
  } else {
    throw new Error("user is undefined")
  }
}
```


```ts {all|14|all}
function createUser(db: Database, user: User) {
  if (user == null) {
    throw new Error("user is undefined")
  }

  if (!db.isConnected()) {
    throw new Error("database not connected")
  }

  if (db.hasEntry(user.email)) {
    throw new Error("user already exists")
  }

  return db.create(user)
}
```

</div>

<p>Where is the core logic in each function?</p>

---
---
# Makes the function requirements transparent

```ts {all|2-4|6-8|10-12|all}
function createUser(db: Database, user: User) {
  if (user == null) {
    throw new Error("user is undefined")
  }

  if (!db.isConnected()) {
    throw new Error("database not connected")
  }

  if (db.hasEntry(user.email)) {
    throw new Error("user already exists")
  }

  return db.create(user)
}
```
<v-click>
  <p>Establishes a "contract" for this function.</p>
</v-click>

---
---
# Cleaner diffs

<p>Let's compare the what the diffs would look like</p>

````md magic-move
```diff
 // without the guard clauses 
 function createUser(db: Database, user: User) {
   if (user != null) {
     if (db.isConnected()) {
-      return db.create(user) 
+      if (!db.hasEntry(user.email)) {
+        return db.create(user)
+      } else {
+        throw new Error("user already exists")
+      }
     } else {
       throw new Error("database not connected")
     }
   } else {
     throw new Error("user is undefined")
   }
 }
```

```diff
 // with the guard clauses
 function createUser(db: Database, user: User) {
   if (user == null) {
     throw new Error("user is undefined")
   }
 
   if (!db.isConnected()) {
     throw new Error("database not connected")
   }

+  if (db.hasEntry(user.email)) {
+    throw new Error("user already exists")
+  }

   return db.create(user)
 }
```
````

---
---
# Exceptions

As with anything in software engineering, there's exceptions to the rules

---
---
# Shameless Plug

I wrote a blog post on this topic, check it out if you're interested.

<!-- Add QR code to the post -->

<a href="https://dev.to/behlers"> dev.to/behlers</a>

<a href="https://x.com/brendenehlers"><carbon-LogoX /> @brendenehlers</a>

<a href="https://www.linkedin.com/in/brendenehlers"><carbon-LogoLinkedin /> Brenden Ehlers</a>

---
layout: end
---
# Thanks!

Any questions?