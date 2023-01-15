---
cover: ''
date: 2022-09-04
datetime: 2022-09-04 00:00:00+00:00
description: Setting up the ipython extension is completely optional, and not You
  can add markata to your I don If you have the extension active an instance will
  automatical
edit_link: https://github.com/edit/main/pages/ipython.md
jinja: false
long_description: Setting up the ipython extension is completely optional, and not
  You can add markata to your I don If you have the extension active an instance will
  automatically be created and If you opt out of setting up the extension or use something
  other than i
now: 2023-01-15 20:28:41.795719
path: pages/ipython.md
published: true
slug: ipython
status: draft
super_description: Setting up the ipython extension is completely optional, and not
  You can add markata to your I don If you have the extension active an instance will
  automatically be created and If you opt out of setting up the extension or use something
  other than ipython Once you have an instance of  The map function func filter sort
  reverse
tags:
- home
- meta
templateKey: ''
title: Loading Markata into Ipython
today: 2023-01-15
---

## Ipython extension

Setting up the ipython extension is completely optional, and not
required, but there for pure convenience.

You can add markata to your
`~/.ipython/profile_default/ipython_config.py` as reccomended by
ipython with the snippet below.

``` python
c.InteractiveShellApp.extensions.append('markata')
```

I don't prefer this because I also have ipython installed in
environments without markata installed, so I do the following in
my personal config so that it does not error when missing markata.

``` python
import importlib


def activate_extension(extension):
    try:
        mod = importlib.import_module(extension)
        getattr(mod, "load_ipython_extension")
        c.InteractiveShellApp.extensions.append(extension)
    except ModuleNotFoundError:
        "extension is not installed"
    except AttributeError:
        "extension does not have a 'load_ipython_extension' function"


extensions = ["markata", ]
for extension in extensions:
    activate_extension(extension)
```

## Loading a markata instance

If you have the extension active an instance will automatically be created and
available as `m` as well as `markata`.

``` python
m
# or
markata
```

If you opt out of setting up the extension or use something other than ipython
you can make an instance yourself.

``` python
from markata import Markata

m = Markata()
```

## Looking through articles

Once you have an instance of `markata` in memory you can look through your
articles using the list of articles, or the map function.


``` python
# get a list of frontmatter.Post objects
m.articles

# leverage the map function to filter
m.map('post', filter='"python" in tags')
m.map('post', filter='date>today')
```

## Map

The map function 

`func`: What to return as the item in the list. This can ve a single attribute
like `title`, or `tags`, or the full post `post`.  It can also be any string of
python like `'date>today'` or something more complicated like
`f'''"{markata.config['url']}/" + slug'''`

``` python
m.map('post')
m.map('title')
m.map('slug')

m.map('"python" in tags')
m.map(f'''"{markata.config['url']}/" + slug''')
```

`filter`: Filter is also just a string of python similar to the `func`
argument, but it filters based on the boolean value of the result.  You can do
things like look for published posts `published`, check for posts posted before
today `date<today`, or articles with certain tags `"python" in tags`.

``` python
m.map(filter='published')
m.map(filter='date<today')
m.map(filter='"python" in tags')
```

`sort`: Sort will try to sort your articles based on the value returned.

``` python
m.map(sort='title')
m.map(sort='date')
m.map(sort='order')
```

`reverse`: Reverse the results returned by map with the `reverse` flag.

``` python
m.map(reverse=False)
m.map(reverse=True)
```
<div class='prevnext'>

    <style type='text/css'>

    :root {
      --prevnext-color-text: #eefbfe;
      --prevnext-color-angle: #e1bd00c9;
      --prevnext-subtitle-brightness: 3;
    }
    [data-theme="light"] {
      --prevnext-color-text: #1f2022;
      --prevnext-color-angle: #ffeb00;
      --prevnext-subtitle-brightness: 3;
    }
    [data-theme="dark"] {
      --prevnext-color-text: #eefbfe;
      --prevnext-color-angle: #e1bd00c9;
      --prevnext-subtitle-brightness: 3;
    }
    .prevnext {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: flex-start;
    }
    .prevnext a {
      display: flex;
      align-items: center;
      width: 100%;
      text-decoration: none;
    }
    a.next {
      justify-content: flex-end;
    }
    .prevnext a:hover {
      background: #00000006;
    }
    .prevnext-subtitle {
      color: var(--prevnext-color-text);
      filter: brightness(var(--prevnext-subtitle-brightness));
      font-size: .8rem;
    }
    .prevnext-title {
      color: var(--prevnext-color-text);
      font-size: 1rem;
    }
    .prevnext-text {
      max-width: 30vw;
    }
    </style>
    
    <a class='prev' href='/your-own-style'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>Your Own Style</p>
        </div>
    </a>
    
    <a class='next' href='/jinja'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>Jinja Variables</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>