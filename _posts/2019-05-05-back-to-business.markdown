---
layout: post
title:  "Back to Business"
date:   2019-05-05 18:47:30 -0300
categories: blog jekyll
---
In 2014 I tried to start a blog using GitHub pages but it lasted only one post. Now I'm trying bring it back to life, but the old code wasn't work with new libraries.

I had to reinstall Jekyll bundle and create a new project from scratch. This proved so far to be better than fixing the old blog, as the new Jekyll is most robust. Just had to discover that most of the files come insied the theme bundle, so for the minima theme we need to get the files from the gem location:

{% highlight Plain Text%}
/Library/Ruby/Gems/2.3.0/gems/minima-2.5.0
{% endhighlight %}

Copy the file that need to customize to the page home directory and them do the changes. It gets a little work but the initial project gets clearer.