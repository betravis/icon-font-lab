---
layout: basic
title: Exercise 2, PUA Icon Font
---
# Exercise 2

## Creating a Private Use Area Icon Font

This is the second exercise in a series on creating icon fonts using FontForge. You may want to at least skim the [first one][exercise-01] if you haven't yet. Most notably, before you start, you will need the [resources][repo] for this lab, an installation of [FontForge][fontforge], and a basic understanding of how to use it.

Before we get started, it would probably be helpful to explain what the Unicode Private Use Area is. [Unicode][unicode] is a way of mapping machine representations of a character (called a code point, it's basically just a number), to a symbol in a writing system, like "a" or "!". While most of these code points are reserved as part of some writing system or other (eg, Latin, Cyrillic, Korean), there are some ranges that are set aside as [Private Use Areas][pua]. These areas are not and will not be mapped by Unicode, and can instead be used for anything you might need, like icons.

One of the reasons for using the Private Use Area for icons is that it is more semantic. The letter `C` means something as part of a writing system, so it's a bit of a hack to replace it visually with something that is not a `C`. The Private Use Area is reserved for custom glyphs, so you might as well take advantage of it.

Ok, enough background, let's get started.

## Step 1: Setup

You can start this lab right where you left off in the [previous one][exercise-01]. Alternatively, if you want to make a clean start, fire up FontForge and open up `bunny-sans-ascii.svg` in the `02-pua` folder from this lab's resources.

![Bunny Sans Start][bunny-sans-start]
{: .figure }

## Step 2: Change the Font Encoding to Unicode

Currently, the font encoding only includes mappings for the Latin characters. We want to switch to the Unicode encoding, to make sure we include the Private Use Area characters. With the font open, choose `Encoding > Reencode > ISO 10646-1 (Unicode, BMP)`. This will add slots for all of the Unicode glyphs in the Basic Multilingual Plane (which is a bit smaller than the full Unicode set of glyphs).

## Step 2: Copy Glyphs

![Unicode Encoding][unicode-encoding]
{: .figure }

What you'll notice is that your table of glyphs grew a lot bigger. Not to worry, you will only be adding two. But, the increased size of the table can make it a bit tricky to navigate. We're going to add outlines to the Private Use Area glyphs at `U+E400` and `U+E401`.

1. Select the `C` glyph (the carrot bunny)
2. Select `Edit > Copy (Cmd/Ctrl+C)` to copy the glyph outline
3. Select `View > Goto`
4. Enter `u+e400` to jump to the `U+E400` glyph
5. Select `Edit > Paste` to paste the glyph outline

![Goto][goto]
{: .figure }
![E400 Added][e400-added]
{: .figure }

You should see something like the above. Now that you've added a glyph way out here, you can navigate back and forth in the table using `View > Next Defined Glyph` and `View > Prev Defined Glyph`.

Feeling pretty good? Try going back and repeating the process for `H` and `u+e401`.

## Step 3: Export

You can now export using the same process as in the [first exercise][exercise-01]. To recap:

1. Select `File > Generate Fonts`
2. Choose `Web Open Font` as the type
3. Deselect `Validate before saving`
4. Save `BunnySans.woff`

If you need more browser support than [woff][woff-support], you can always use a font kit generator like [Font Squirrel][font-squirrel-generator].

Pro tip: The general way of using these is in HTML with character entities like `&#xe400;`, or in CSS with before/after pseudo-elements like `content: "\e400";`.

## Wrapup

That's all there is to it. If you want to see it in use, check out this [example][result].

Questions, comments, bugs?
File an [issue][issues] or shoot off a [tweet][twitter].

As always, the font used is [Open Sans][open-sans], with bunny graphics by [Brad Ashburn][bashburn].

[exercise-01]: ../01-ascii
[fontforge]: http://fontforge.github.io/
[open-sans]: http://www.google.com/fonts/specimen/Open+Sans
[repo]: https://github.com/betravis/icon-font-lab
[pua]: http://en.wikipedia.org/wiki/Private_Use_Areas
[unicode]: http://en.wikipedia.org/wiki/Unicode
[woff-support]: http://caniuse.com/#feat=woff
[font-squirrel-generator]: http://www.fontsquirrel
[bashburn]: http://thenounproject.com/bashburn
[issues]: https://github.com/betravis/icon-font-lab/issues
[twitter]: http://twitter.com/bear_travis
[result]: ../02-pua-result

[bunny-sans-start]: img/bunny-sans-start.png
[goto]: img/goto.png
[goto-result]: img/goto-result.png
[e400-added]: img/e400-added.png
[unicode-encoding]: img/unicode-encoding.png
