---
layout: post
title:  "Easier Python paths"
date:   2018-05-09 16:19:35 -0600
categories: jekyll update
---

I was recently writing some Python scripts that needed to be a lot of file path
manipulation, often using the same path prefixes repeatedly, and I was getting
annoyed with having to type `os.path.join(... , ...)` all the time. To save my
typing fingers I wrote a [handy little helper](https://gist.github.com/nickovs/cec1e1624b47224e0492d17e30a2addb) class:

{% highlight python %}
class PathPrefix(str):
    def __truediv__(self, other):
        return PathPrefix(os.path.join(self, other))
{% endhighlight %}

Now appending things onto the ends of paths looks far more natural (unless you are used to Windows path seperators):

{% highlight python %}
path = PathPrefix("/some/path")
file1 = path / "file1"
sub_file = path / "subdir" / "file2"
{% endhighlight %}

I think this might be the most useful three lines of code I've written in a while!

