---
cover: ''
date: 2022-09-02
datetime: 2022-09-02 00:00:00+00:00
description: The first thing you will want to do is make sure that you can build your
  site and see it in the browser.  Markata builds static websites using a python based
  cl
edit_link: https://github.com/edit/main/pages/building-the-site.md
jinja: false
long_description: The first thing you will want to do is make sure that you can build
  your site and see it in the browser.  Markata builds static websites using a python
  based cli that can be setup with very few steps once you have python 3.7+ installed.  You
  will hav
now: 2023-01-15 20:28:41.795708
path: pages/building-the-site.md
published: true
slug: building-the-site
status: draft
super_description: The first thing you will want to do is make sure that you can build
  your site and see it in the browser.  Markata builds static websites using a python
  based cli that can be setup with very few steps once you have python 3.7+ installed.  You
  will have to become at least a little bit comfortable running some commands from
  the command line to run the build. This site comes with a  Hatch comes with a nice
  system for creating scirpts that you can run in your Once you have the site up and
  running, op
tags:
- home
- meta
templateKey: ''
title: Building the Site
today: 2023-01-15
---

The first thing you will want to do is make sure that you can build your site and see it in the browser.  Markata builds static websites using a python based cli that can be setup with very few steps once you have python 3.7+ installed.  You will have to become at least a little bit comfortable running some commands from the command line to run the build.


## Installation

This site comes with a `pyproject.toml` that can be used by hatch to
automatically take care of your virtual environments for you.

``` bash
pip install hatch
```

## Building the site, Leveraging Hatch

Hatch comes with a nice system for creating scirpts that you can run in your
managed virtual environment with less effort of managing.  You can create any
that you want in your own `pyproject.toml`, but these come with the template
out of the box.

``` bash
# builds the site
hatch run build

# clean's cache and output directory
hatch run clean

# clean's cache and output directory, and builds
hatch run clean-build

# runs a development server, watches for changes and rebuilds.
hatch run tui

# run's clean then start's the tui
hatch run clean-tui

# just serve markout at localhost:8000
hatch run serve
```

Once you have the site up and running, open your browser to
[http://localhost:8000](http://localhost:8000).

> Note,if you already have something running on port `8000` hatch run serve will give
> you an error, but hatch run tui will automatically choose the next available port.
> Make sure you open the right link in your browser.

## Building the site, vanilla

You will want to install everything in a virtual environment to prevent
yourself from clogging up your system python, or trying to run two versions of
`markata` for different projects.

``` bash
# using hatch for the virtual environment
hatch shell

# using venv
python -m venv .venv
. ./.venv/bin/activate
pip install -e .
```

Once you have your virtual environment created and activated you can use the
markata cli plugin to build your site.

``` bash
# builds the site
markata build

# clean's cache and output directory
markata clean

# runs a development server, watches for changes and rebuilds.
markata tui
```

## repl or script

It's also possible to run the build from a repl like ipython or a python
script.

``` python
from markata import Markata

m = Markata()
m.run()
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
    
    <a class='prev' href='/jinja'>
    

        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.5 8.25L9.75 12L13.5 15.75" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"> </path>
        </svg>
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>prev</p>
            <p class='prevnext-title'>Jinja Variables</p>
        </div>
    </a>
    
    <a class='next' href='/'>
    
        <div class='prevnext-text'>
            <p class='prevnext-subtitle'>next</p>
            <p class='prevnext-title'>Markata Blog Starter</p>
        </div>
        <svg width="50px" height="50px" viewbox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10.5 15.75L14.25 12L10.5 8.25" stroke="var(--prevnext-color-angle)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
    </a>
  </div>