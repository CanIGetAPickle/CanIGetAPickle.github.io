---
layout: post
title: Sinatra Blackjack Error
---

## Ughhhh...

Errors are nothing new to me, and I've gotten pretty comfortable with deciphering them on my own (and with a little help from Google). This one had me stumped, though: 

```
ArgumentError - wrong number of arguments (1 for 0): 
/home/action/.rvm/gems/ruby-1.9.3-p551/gems/sinatra-1.4.5/lib/sinatra/base.rb:302:in 'session'
...
```

The stack trace was long and not very helpful, mainly pointing me to files I don't have access to and/or don't know anything about. It spit out all sorts of words I don't recall using, like "undefined method join" and "unexpected keyword ensure" (which I later found out about <a href="http://www.skorks.com/2009/09/ruby-exceptions-and-exception-handling/">here</a>).

I spent at least 2 hours going through my code, comparing it with other sources, even rebuilding parts from scratch.

Then, upon <a href="https://github.com/staycreativedesign">Gustavo</a> gracing me with his virtual presence, I found the source of my pain and suffering:

```
<%= session[:player_name] %> has <%= session [:player_pot] %> and bet $<%= session[:player_bet] %> this round.
```

See it? Ahhh, yes. That one little space between "session" and "[:player_pot]" caused my entire app to lash out like <a href="https://www.youtube.com/watch?v=gp-Gu4OkJ2Y">John McEnroe at Wimbledon 1981</a>.

Sinatra: 1

Dan: 0
