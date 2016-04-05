---
layout: post
comments: true
html2canvas: true
title:  "The Beginning"
date:   2016-04-05
categories: update
---
This is the first post, mainly to test Jekyll and github pages. Also to test Disqus.

Making a trie in python
{% highlight python %}
def make_trie(*words):
     root = dict()
     for word in words:
         current_dict = root
         for letter in word:
             current_dict = current_dict.setdefault(letter, {})
         current_dict[_end] = _end
     return root

def in_trie(trie, word):
    current_dict = trie
    for letter in word:
        if letter in current_dict:
            current_dict = current_dict[letter]
        else:
            return False
    else:
        if _end in current_dict:
            return True
        else:
            return False

>>>make_trie('foo', 'bar', 'baz', 'barz')
{'b': {'a': {'r': {'_end_': '_end_', 'z': {'_end_': '_end_'}}, 
             'z': {'_end_': '_end_'}}}, 
 'f': {'o': {'o': {'_end_': '_end_'}}}}
>>> in_trie(make_trie('foo', 'bar', 'baz', 'barz'), 'baz')
True
>>> in_trie(make_trie('foo', 'bar', 'baz', 'barz'), 'barz')
True
>>> in_trie(make_trie('foo', 'bar', 'baz', 'barz'), 'barzz')
False
>>> in_trie(make_trie('foo', 'bar', 'baz', 'barz'), 'bart')
False
>>> in_trie(make_trie('foo', 'bar', 'baz', 'barz'), 'ba')
False

{% endhighlight %}

100% stolen from a [Stack Overflow post][overflow] and highly not recommended for interviews.

[overflow]: http://stackoverflow.com/questions/11015320/how-to-create-a-trie-in-python