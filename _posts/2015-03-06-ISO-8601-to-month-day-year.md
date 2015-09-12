---
layout: post
title: ISO 8601 to Month-Day-Year
---

## What the heck is that?

I was creating a small project using the YouTube API. Each video has a "snippet" of information available. One property of such a snippet is "publishedAt" (`snippet.publishedAt`) which returns a *datetime* value ([documentation](https://developers.google.com/youtube/v3/docs/playlistItems)). <!--end-excerpt-->

Little did I know, that *datetime* value would be the ugliest duckling on the page: `2015-03-05T19:27:39Z`.

Overcome with dread, I couldn't help but ponder, "*What the heck is that?*"

Turns out that's a standard called **ISO 8601**. Basically, it spits out the date and time in the format YYYY-MM-DDThh:mm:ss.sZ. You can look up the history on your own, I won't bore you here. Instead, let me show you the fix:

{% highlight javascript %}
  function addZero(i) {
    if (i < 10) {
      i = "0" + i;
    }
    return i;
  }
  
  var timeStr = videoDate;
  var date = new Date(timeStr);
  var day = date.getDate();
  var year = date.getFullYear();
  var month = date.getMonth()+1; // Months begin at 0
  var hours = date.getHours();
  var minutes = addZero(date.getMinutes());
  var dateStr = month+"/"+day+"/"+year+" at "+hours+":"+minutes;
{% endhighlight %}

This tucked a nice "MM/DD/YYYY at HH:MM" string into the *dateStr* variable that I could concatenate into my javascript/html.
As you might have noticed, I also included the time here. I created a function called *addZero* to add a '0' before minutes less than 10 (otherwise it would show up "12:9" instead of "12:09"; [source](http://www.w3schools.com/jsref/jsref_getminutes.asp)). Also worth noting, months are numbered 0-11, so you need to add 1.

### References
<a href="http://www.w3schools.com/jsref/jsref_obj_date.asp" target="_blank">JavaScript Date Reference</a>
<a href="http://stackoverflow.com/questions/12498619/convert-iso-8601-time-date-into-plain-english" target="_blank">Stack Overflow - Convert ISO 8601 time date into plain English</a>