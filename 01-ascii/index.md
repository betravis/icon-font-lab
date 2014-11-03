---
layout: basic
title: Exercise 1, ASCII Icon Font
---
#Exercise 1
An ASCII Icon Font

I had to create an icon font the other day to demonstrate the [different ways][icon-methods] of building an icon font. I figured I would document how to make one using FontForge, in case you ever have to make or adjust one by hand.

A couple notes before we get started. Icon fonts are just one way of using icons. The other current major players are vector and raster image icons. Filament Group detailed some of the finer points of icon fonts vs vector icons in [bulletproof icon fonts][bulletproof-icon-fonts]. In general, the trend I see today is using SVG icons where possible with PNG fallback. Also, when packaging a large number of icons into a font, it will probably be easier to use a tool, either a GUI based tool like [Icomoon][icomoon] or [Fontello][fontello] or a build script like [Font Custom][font-custom].

*breathe*

What we're going to be doing today is replacing some characters in a font (Open Sans) with different bunny icons. We'll be replacing the capital letters 'C' and 'H' to represent a bunny with a carrot, and a happy bunny. Later articles will explain how to do some fancier character to icon mappings.

## Step 1: Setup

First up, you'll need to install FontForge. Visit their [site][fontforge] and follow the installation instructions. It can be a little daunting, but they try to make it as simple as possible.

Next, you'll need to [grab the resources][repo] for this lab. You can clone the repository, or just download the zip (click the `Download Zip` button in the lower right). All the materials for this lab, including these instructions, are in the `01-ascii` folder.

## Step 2: Open the Starter Font

Next up, open up FontForge. After it's open, you will need to open the `bunny-sans.svg` font. This is a clipped trimmed down set of glyphs from [Open Sans][open-sans]. We're starting with an existing font so you don't have to set everything up from scratch, but you could easily create a new font in FontForge as well.

To open `bunny-sans.svg`, choose `File > Open`. The file picker is a bit different than your standard OS dialog, and will probably start you out at the root of your OS disk. You can click the `Home` button in the upper left to take you to your home folder.

![File Picker][file-picker-img]
{: .figure}

## Step 3: Swap out the C Glyph

![Font Mapping][font-mapping-img]
{: .figure}

When you have opened up `bunny-sans.svg`, you should see something like the above image.

FontForge's main view of a font is as a table of glyphs. Each glyph maps a character code to a path representing its visual outlines. Think of a character code as what you would type on your keyboard, and the path outlines as what your display would show you. The character code is in the blue outlined box, while the outlines are displayed below.

We're going to edit the `C` (that's a capital) first. You can do this by double clicking it, or by selecting it and choosing `Glyph Info` from the `Element` menu at the top of the screen. When you do this, you will get a view of the glyph outline that you can edit. It should look like the below.

![Glyph Outline][glyph-outline-img]
{: .figure}

You can 
[icon-methods]: http://betravis.github.io/icon-methods/
[icon-talk]: http://betravis.github.io/icons-and-the-web/
[icon-font-mappings]: http://blogs.adobe.com/webplatform/2013/01/15/icons-and-icon-fonts/
[bulletproof-icon-fonts]: http://www.filamentgroup.com/lab/bulletproof_icon_fonts.html 
[fontello]: http://fontello.com/
[icomoon]: http://icomoon.io
[font-custom]: http://fontcustom.com/
[fontforge]: http://fontforge.github.io/
[open-sans]: http://www.google.com/fonts/specimen/Open+Sans

[file-picker-img]: img/file-picker.png "File Picker"
[font-mapping-img]: img/font-mapping.png "Font Mapping"
[glyph-outline-img]: img/glyph-outline.png "Glyph Outline"
