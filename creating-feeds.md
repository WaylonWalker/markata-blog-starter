---
cover: ''
date: 2022-09-05
datetime: 2022-09-05 00:00:00+00:00
description: Feeds are a powerful feature of  Now create an instance of markata. Now
  you should be able to list out the articles, for this site it will be something
  like. No
edit_link: https://github.com/edit/main/pages/creating-feeds.md
jinja: false
long_description: 'Feeds are a powerful feature of  Now create an instance of markata.
  Now you should be able to list out the articles, for this site it will be something
  like. Now let Now if you wanted to filter for only published posts, you can filter
  by the boolean '
now: 2023-01-15 20:28:41.795714
path: pages/creating-feeds.md
published: true
slug: creating-feeds
status: draft
super_description: 'Feeds are a powerful feature of  Now create an instance of markata.
  Now you should be able to list out the articles, for this site it will be something
  like. Now let Now if you wanted to filter for only published posts, you can filter
  by the boolean variable  And a little more arbitrary, and slightly more complex
  filter. The same results can be achieved with the  Then we can add the filter for  And
  the more arbitrary filter looking for  Since each article is unpacked into the map
  function, path '
tags:
- home
- meta
templateKey: ''
title: Creating Your Feeds
today: 2023-01-15
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

## Let's poke through our articles

Now you should be able to list out the articles, for this site it will be something like.

``` python
m.articles
# [
#     <frontmatter.Post object at 0x7f609831b0a0>,
#     <frontmatter.Post object at 0x7f6098318b80>,
#     <frontmatter.Post object at 0x7f609831a890>,
#     <frontmatter.Post object at 0x7f609831ab30>,
#     <frontmatter.Post object at 0x7f609831aa70>,
#     <frontmatter.Post object at 0x7f609831b760>
# ]
```

Now let's say you want the title for all the articles, you could do this with a list comp.

``` python
[post['title'] for post in markata.articles]
# ['Building the Site', 'Home Page', 'Loading Markata into Ipython', 'Jinja Variables', 'Your Own Style', '404']
```

Now if you wanted to filter for only published posts, you can filter by the boolean variable `published`.

``` python
[post['title'] for post in markata.articles if published]
# ['Building the Site', 'Home Page', 'Loading Markata into Ipython', 'Jinja Variables', 'Your Own Style']
```

And a little more arbitrary, and slightly more complex filter.

``` python
[post['title'] for post in markata.articles if "y" in post['path']]
# ['Loading Markata into Ipython', 'Your Own Style']
```

## Using map

The same results can be achieved with the `Markata.map` function.  Again let's
start by getting the title.

``` python
[post['title'] for post in markata.articles if published]
markata.map('title')
# ['Building the Site', 'Home Page', 'Loading Markata into Ipython', 'Jinja Variables', 'Your Own Style', '404']
```

Then we can add the filter for `published` posts back in.

``` python
markata.map('title', filter='published')
# ['Building the Site', 'Home Page', 'Loading Markata into Ipython', 'Jinja Variables', 'Your Own Style', '404']
```

And the more arbitrary filter looking for "y" in the article's path.

``` python
markata.map('title', filter='"y" in post["path"]')
# ['Loading Markata into Ipython', 'Your Own Style']
```

Since each article is unpacked into the map function, path is also directly
available to the filter, so we don't necessarily need to reach for the `post`.

``` python
markata.map('title', filter='"y" in path')
# ['Loading Markata into Ipython', 'Your Own Style']
```

Lastely we can also **sort on date**, by adding a sort argument.

``` python
markata.map('title', filter='published', sort='date')
# ['Building the Site', 'Home Page', 'Loading Markata into Ipython', 'Jinja Variables', 'Your Own Style', '404']
```

## What does this have to do with feeds.

Markata can make a feed page, displaying each post in the returned list inside
of an html feed.  It does this by unpacking the arguments from the feeds config
into the map function.

``` python
[markata.feeds.published]
# creates a feed at /published
filter="date<=today and post.get('published', False)"
sort="date"
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
    
    <a class='prev' href='/404'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>Whoops that page was not found</p>
        </div>
    </a>
    
    <a class='next' href='/your-own-style'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>Your Own Style</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>