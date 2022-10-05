---
date: 2022-09-05 1:00:00
title: Your Own Style
published: True
tags:
  - home
  - meta

---

Feeds are a powerful feature of `markata` that allow you to build feeds of
posts from the same arguments that get passed into `Markata.map`, all within
`markata.toml`.  You can create feeds for things like your published articles,
articles that contain a certain tag, articles that are stored in a certain
folder, articles posted before or after a certain date (likely today).

## Load up ipython

_or python or a script that you run, whatever your fancy_

Now create an instance of markata.

``` python
from markata import Markta
m = Markata()
```

Now you should be able to list out the articles, for this site it will be something like.

``` python
m.articles
# [{% for post in markata.articles %}{{post}}{%% endfor %}]
```

