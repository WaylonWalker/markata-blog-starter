---
config_overrides:
  head:
    text: "<style>\n    ul {\n        list-style-type: None;\n    }\n    li a {\n
      \       background: rgba(255,255,255,.1);\n        margin: .2rem;\n    }\n</style>\n"
cover: ''
date: 2022-09-03
datetime: 2022-09-03 00:00:00+00:00
description: Markata uses python The veresion of markata used to build the site. ({{  A
  python datetime object. ({{date.today()}}) All variables from your post frontmatter
  l
edit_link: https://github.com/edit/main/pages/jinja.md
jinja: false
long_description: Markata uses python The veresion of markata used to build the site.
  ({{  A python datetime object. ({{date.today()}}) All variables from your post frontmatter
  like  The last variable exposed is an instance of  You can also map over posts to
  get more.
now: 2023-01-15 20:28:41.795689
path: pages/jinja.md
published: true
slug: jinja
status: draft
super_description: Markata uses python The veresion of markata used to build the site.
  ({{  A python datetime object. ({{date.today()}}) All variables from your post frontmatter
  like  The last variable exposed is an instance of  You can also map over posts to
  get more. {% for post in markata.map( [ {% for post in markata.map( [
tags:
- home
- meta
templateKey: ''
title: Jinja Variables
today: 2023-01-15
---

Markata uses python's powerful jinja2 templating library for its templates as well as giving authors the ability to inject variables right into their markdown posts. This post contains quite a few examples of using jinja variables, compare it's output in the browser to the raw markdown file in `pages/jinja.md`.

### `__version__`

The veresion of markata used to build the site. (0.5.3)

### date

A python datetime object. (2023-01-15) 

### Frontmatter

All variables from your post frontmatter like `title` (Jinja Variables) and `tags` (['home', 'meta']). If you are not familiar with frontmatter it's the content at the top
of a markdown file between `---`.  Markata uses the most common type of
frontmatter, `yaml`.

```md
---
# this is the frontmatter
date: 2022-09-29 13:26:33
title: Home Page

---

## the post

markdown gets written after the frontmatter

```

##  markata

The last variable exposed is an instance of `markata.Markata` called `markata`.
This allows you to reference all of your other posts in very interesting ways.
such as getting the latest post -> [Creating Your Feeds](/creating-feeds)

You can also map over posts to get more.

## Last Three Posts


*  [Creating Your Feeds](creating-feeds)
*  [Your Own Style](your-own-style)
*  [Loading Markata into Ipython](ipython)

## Last Three Python posts


*  [Creating Your Feeds](creating-feeds)
*  [Your Own Style](your-own-style)
*  [Loading Markata into Ipython](ipython)
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
    
    <a class='prev' href='/ipython'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>Loading Markata into Ipython</p>
        </div>
    </a>
    
    <a class='next' href='/building-the-site'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>Building the Site</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>