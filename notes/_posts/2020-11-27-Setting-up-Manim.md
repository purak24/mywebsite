---
layout: post
title: Setting up Manim and creating first animation in under 15 minutes
summary: Walk-through for installing Manim
category: note
---

> Walk-through for installing Manim aka Mathematical Animation Package on Mac.

## Step 1: Install Dependencies

![Parts of Manim]({{site.baseurl}}/assets/manim_installation_1.jpeg)

{% highlight js %}
// Install Cairo
brew install cairo

// Install Pango
brew install pkg-config
brew install libffi
brew install pango
brew install glib

// Install FFmpeg
brew install ffmpeg

// Install Basic Latex
brew cask install basictex
sudo tlmgr install standalone preview doublestroke relsize fundus-calligra wasysym physics dvisvgm.x86_64-darwin dvisvgm rsfs wasy cm-super
{% endhighlight %}

## Step 2: Install Manim

{% highlight js %}
pip3 install manimce
{% endhighlight %}

## Step 3: Set up a Manim project

Set up a project folder and create an empty python file.

![Set up a project folder and create an empty python file]({{site.baseurl}}/assets/manim_file.png)

Then add the following code in it.

```python
from manim import *
class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()                   # create a circle
        circle.set_fill(PINK, opacity=0.5)  # set the color and transparency
        self.play(ShowCreation(circle))     # show the circle on screen
```

And run:

```
$ manim scene.py SquareToCircle -pl
```

Note: If you see an error like:

```
ModuleNotFoundError: No module named 'pangocairocffi._generated.ffi'
```

Then run:

```
$ pip3 uninstall pangocairocffi cairocffi
$ pip3 install --no-binary :all: -U pangocairocffi --no-cache
```

## Step 4: You first animation scene using Manim!

<video autoplay controls loop="loop">
  <source src="/assets/SquareToCircle.mp4"/>
</video>
