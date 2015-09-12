---
layout: post
title: Sinatra Blackjack Error
---

## Ughhhh...

Errors are nothing new to me, and I've gotten pretty comfortable with deciphering them on my own (and with a little help from Google). This one had me stumped, though: <!--end-excerpt-->

```
ArgumentError - wrong number of arguments (1 for 0): 
/home/action/.rvm/gems/ruby-1.9.3-p551/gems/sinatra-1.4.5/lib/sinatra/base.rb:302:in 'session'
...
```

The stack trace was long and not very helpful, mainly pointing me to files I don't have access to and/or don't know anything about. It spit out all sorts of words I don't recall using, like "undefined method join" and "unexpected keyword ensure" (which I later found out about <a href="http://www.skorks.com/2009/09/ruby-exceptions-and-exception-handling/" target="_blank">here</a>).

I spent at least 2 hours going through my code, comparing it with other sources, even rebuilding parts from scratch.

Then, upon <a href="//github.com/staycreativedesign" target="_blank">Gustavo</a> gracing me with his virtual presence, I found the source of my pain and suffering:

{% highlight ruby %}
<%= session[:player_name] %> has <%= session [:player_pot] %> and bet $<%= session[:player_bet] %> this round.
{% endhighlight %}

See it? Ahhh, yes. That one little space between "session" and "[:player_pot]" caused my entire app to lash out like <a href="//www.youtube.com/watch?v=C8Nyc9jzSDg" target="_blank">John McEnroe at Stockholm 1984</a>.

Sinatra: 1

Dan: 0
