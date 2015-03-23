---
layout: post
title: Resetting Heroku Database
---

## There's a command for everything

I've been working on a very simple Pinterest clone and ran into a slight issue (read: headache). I thought I took extra care to ensure I deleted all of my test "pins" before installing devise. It turns out I accidentally deleted them in my development environment instead of my production environment. 

When I went to test out the app on Heroku, there were a couple of stray pins that I didn't want around. I hit the "destroy" link, but was prompted with the error "You're not authorized to edit this pin." (Couldn't really complain about devise kicking in successfully, though.) So my first thought was, "Okay, comment out some of the devise stuff to bypass authentication." Sadly, that resulted in a mess of errors due to all of the devise methods scattered about my code. 

### StackOverflow to the rescue!

A quick Google search (which never comes soon enough in cases like this) revealed the perfect solution: 
```heroku pg:reset DATABASE```

This turned out to be the perfect solution. Because I only created two user accounts and two pins, I didn't mind wiping the whole database. Definitely not something you want to use if your app is already up and running with live users and content.


### References
[Stack Overflow - How to empty DB in heroku](http://stackoverflow.com/questions/4820549/how-to-empty-db-in-heroku)
