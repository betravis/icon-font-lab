---
layout: basic
title: Exercise 1, ASCII Icon Font
---
# Exercise 1

## Creating An ASCII Icon Font

I had to create an icon font the other day to demonstrate the [different ways][icon-methods] of using icons (including icon fonts). I figured I would document how to make one using FontForge, in case you ever have to make or adjust one by hand.

A couple notes before we get started. Icon fonts are just one way of using icons. The other current major players are vector and raster image icons. CSS-Tricks has a [comparison of fonts and SVG icons][css-tricks-fonts-vs-svg]. In general, the trend I see today is using SVG icons where possible with PNG fallback. You may still find icon fonts fit your situation best, but it's worth considering other options too. Finally, if you are routinely packaging a large number of icons into a font, it will probably be easier to use a tool, either a GUI based tool like [Icomoon][icomoon] or [Fontello][fontello] or a build script like [Font Custom][font-custom].

## Ready?

What we're going to be doing today is replacing some characters in a font with bunny icons. We'll be replacing the capital letters 'C' and 'H' to represent a bunny with a carrot, and a happy bunny, respectively. Later articles will explain how to do some fancier character to icon mappings.

![Carrot Bunny][carrot-bunny-svg] ![Happy Bunny][happy-bunny-svg]
{: .figure .icons }

## Step 1: Setup

First up, you'll need to install FontForge. Visit their [site][fontforge] and follow the installation instructions. It can be a little daunting, but they try to make it as simple as possible.

Next, you'll need to grab the [resources][repo] for this lab. You can clone the repository, or just download the zip (click the `Download Zip` button in the lower right). All the materials for this lab, including these instructions, are in the `01-ascii` folder.

## Step 2: Open the Starter Font

Next up, open up FontForge. After it's open, you will need to open the `bunny-sans.svg` font via `File > Open`. The file picker is a bit different than your standard OS dialog, and will probably start you out at the root of your OS disk. You can click the `Home` button in the upper left to take you to your home folder.

![File Picker][file-picker-img]
{: .figure}

Bunny Sans is a trimmed down set of glyphs from [Open Sans][open-sans]. We're starting with an existing font so you don't have to set everything up from scratch, but you can also create a font entirely from scratch with FontForge.

## Step 3: Swap out the C Glyph

![Font Mapping][font-mapping-img]
{: .figure}

When you have opened up `bunny-sans.svg`, you should see something like the above image.

FontForge's main view of a font is as a table of glyphs. Each glyph maps a character code to a path representing its visual outline. Think of a character code as what you would type on your keyboard, and the path outlines as what your display would show you, using a font to map one to the other. The character code is in the blue outlined box, while the outlines are displayed below.

We're going to edit the `C` (that's a capital) first. To do this, you will need to open the glyph info for the letter.

1. Select the `C` in the font info table
2. `Element > Glyph Info` or double click the glyph

When you do this, you will get a view of the glyph outline that you can edit. It should look like the image below.

![Glyph Outline][glyph-outline-img]
{: .figure}

The outline is just a path, in a vector coordinate space set by the font. Each glyph sits within the same vertical coordinate space, but glyphs can have varying widths. I have highlighted the area allocated to the glyph in the image below (the horizontal line about 75% down the blue box is the baseline). The coordinate system's origin is on the left at the baseline, with x and y coordinates increasing towards the upper right.

![Highlighted Glyph Outline][glyph-outline-highlight-img]
{: .figure }

 While FontForge has drawing tools to allow you to manipulate paths by hand, we're just going to import some existing artwork to replace the `C` outline. First, remove the existing artwork.

1. `Edit > Select > Select All` or `Cmd/Ctrl + A`
2. Press the `Delete` or `Backspace` key

Then, import the artwork for the carrot bunny.

1. `File > Import`
2. Make sure `Format: SVG` is selected at the bottom of the dialog
3. Pick `carrot.svg` from the `01-ascii` folder

![Import SVG][svg-import-img]
{: .figure }

You should see a new outline for the glyph like the one below.

![Imported SVG][imported-svg-img]
{: .figure }

This outline needs to be resized a little bit to fit well within the glyph's box. I'd like it to be a little smaller and shifted left and up a little bit. With all of the points selected, do the following.

1. `Element > Transformations > Transform (Cmd/Ctrl + \)`
2. Set up a `Move (-200, 100)`
3. Add a `Scale Uniformly (90%)`
4. Click `Apply` to test out the transform
5. Click `OK`

![Transform Options][transform-img]
{: .figure }

You may be missing out on some of the transformation tools in a program like Illustrator, but this was the fastest way I found to make these adjustments.

## Step 4: Test Out the C Glyph

Next up, let's see what our glyph looks like when used alongside other glyphs.

1. `Metrics > New Metrics Window`
2. Type some characters in the top text input (I typed `AB`)

![Metrics Window][metrics-window-img]
{: .figure }

The window will display the enlarged glyphs below, how they will lay out next to each other. The space between the glyph and its neighbors on the left and right (Left Bearing and Right Bearing) seem a little uneven. You can adjust them here in the `L Bearing` and `R Bearing` cells beneath the `C` in the bottom table. 

1. Replace the `L Bearing` for C (`290.21`) with `100`
2. Replace the `R Bearing` for C (`-166.83`) with `100`

Don't worry if FontForge tweaks your numbers slightly. FontForge is doing its best to match all your constraints, but can't always do so exactly.

Congrats, you've finished editing your first glyph. You can close the metrics and glyph windows.

![Completed Glyph][completed-glyph-img]
{: .figure }

## Step 5: Swap out the H Glyph

Feeling confident? Go ahead and repeat the process for `H` and `happy.svg`.

## Step 6: Export the Font

Go to `File > Generate Fonts`. Choose `Web Open Font`, and save it as `BunnySans.woff`. I would uncheck `Validate Before Saving`, but if you leave it checked, just choose to generate the font despite the validation warnings.

![Generate Woff][generate-woff-img]
{: .figure }

If you're interested in the warnings, see the `Additional Info` section at the bottom.

And that's it, you've got a woff font! If [woff support][woff-support] is good enough, you're done, and can add it to your project. Check out the [result][result] for an example how. If you need more browser support, you can upload the font to a service like the [Font Squirrel Webfont Generator][font-squirrel-generator].

## Closing Thoughts

Substituting icon outlines for standard characters like `C` and `H` is just one way of placing icons in a font. I'm going to cover two more, Private Use Area glyphs and Ligatures, in subsequent articles (for an overview of these different methods, check out [this blog post][icon-font-mappings]). For best practices when using icon fonts, I would also make sure to check out Filament Group's [Bulletproof Icon Fonts article][bulletproof-icon-fonts].

### Questions, comments, bugs?

File an [issue][issues] or fire off a [tweet][twitter].

### Credits

The artwork is by [Brad Ashburn][bashburn], and the font you're editing is [Open Sans][open-sans].

### About the warnings

* *Self intersecting* paths can have rendering issues. You can generally clean this up using `Element > Simplify > Simplify`.
* *Missing points at extrema* on a path can also result in suboptimal rendering. You can fix this up with `Element > Add Extrema`.
* *Non-integral coordinates* can also cause rendering issues, but are very difficult to get right with icon artwork. The automated fixup command is `Element > Round > To Int`, but it will often result in skewed artwork, and bring back your missing points and self-intersecting path validation problems.

[bashburn]: http://thenounproject.com/bashburn
[issues]: https://github.com/betravis/icon-font-lab/issues
[twitter]: http://twitter.com/bear_travis
[icon-methods]: http://betravis.github.io/icon-methods/
[icon-talk]: http://betravis.github.io/icons-and-the-web/
[icon-font-mappings]: http://blogs.adobe.com/webplatform/2013/01/15/icons-and-icon-fonts/
[bulletproof-icon-fonts]: http://www.filamentgroup.com/lab/bulletproof_icon_fonts.html 
[fontello]: http://fontello.com/
[icomoon]: http://icomoon.io
[font-custom]: http://fontcustom.com/
[fontforge]: http://fontforge.github.io/
[open-sans]: http://www.google.com/fonts/specimen/Open+Sans
[repo]: https://github.com/betravis/icon-font-lab
[css-tricks-fonts-vs-svg]: http://css-tricks.com/icon-fonts-vs-svg/
[woff-support]: http://caniuse.com/#feat=woff
[font-squirrel-generator]: http://www.fontsquirrel.com/tools/webfont-generator
[result]: ../01-ascii-result

[file-picker-img]: img/file-picker.png "File Picker"
[font-mapping-img]: img/font-mapping.png "Font Mapping"
[glyph-outline-img]: img/glyph-outline.png "Glyph Outline"
[glyph-outline-highlight-img]: img/glyph-outline-highlight.png "Glyph Outline Highlight"
[svg-import-img]: img/svg-import.png "SVG Import"
[imported-svg-img]: img/imported.png "Imported Outlines"
[transform-img]: img/transform.png "Transform Window"
[metrics-window-img]: img/metrics-window.png "Metrics Window"
[completed-glyph-img]: img/glyph-complete.png "Completed C Glyph"
[generate-woff-img]: img/generate-woff.png "Generate Woff"
[happy-bunny-svg]: happy.svg
[carrot-bunny-svg]: carrot.svg
