---
layout: post
title: Creating temporary directories in Ruby
tags:
- gem
- ruby
- Development
---
How can I easily create temporary directories (and files) in Ruby that won't
break the cross-platform compatibility of my script?

It took a bit of digging to locate this information, so I'll post it here in
the hope that the search engines will make it easier to find for the next
person with this question.

The answer is to use Dir.mktmpdir, which will magically appear in the Dir
class if you require 'tmpdir' in your script. Basically, [tmpdir adds methods
to the existing core Dir class](http://www.ruby-
doc.org/stdlib-1.8.6/libdoc/tmpdir/rdoc/Dir.html). It's apparently been part
of Ruby since 1.8.6.

I would recommend using this standard library rather than rolling your own
because it lets your operating system worry about where to locate the
temporary directory.

![](http://media.tumblr.com/tumblr_lwvqm6EkVK1r3t3xr.png)
