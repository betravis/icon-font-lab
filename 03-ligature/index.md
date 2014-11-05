---
layout: basic
title: Exercise 3, Ligature Icon Font
---
# Exercise 3

## Creating a Ligature Icon Font

Ligatures are a font feature that combine multiple letters into a single visual glyph. They are often used when letters in certain combinations need to be visually adjusted, such as "fi", "ff", or "fl". You can read more about them on [Wikipedia][wikipedia-ligature].

The key takeaway is that you can also use ligatures to replace the name of an icon with the glyph for that icon, like replacing "carrot" with

![Carrot Bunny][carrot]
{: .figure .icons }

This builds on two preview exercises, building an [ascii icon font][exercise-01] and building a [pua icon font][exercise-02]. You can pick up immediately from where *Exercise 2* left off, or fire up [FontForge][fontforge] with the `03-ligature/bunny-sans-pua.svg` file in the [assets][repo] for this lab.

Start off by reencoding the font to use Unicode. [Exercise 2][exercise-02] contains a longer writeup on the reasoning behind this. `Encoding > Reencode > ISO 10646-1 (Unicode, BMP)`.

## Step 1: Add the Ligature Lookup Table

In a font, ligatures are kept in a special lookup table that contains information about what character combinations can map to what glyphs. Each of these tables corresponds to a specific type of lookup, with data about the specific combinations being kept in subtables.

The first thing we have to do is create the ligature lookup table. With your font open:

1. Select `Element > Font Info`
2. Select `Lookups` from the side of the dialog

![Lookups][lookups]
{: .figure }

We are going to add a ligature lookup table, followed by a subtable to contain our specific ligatures. Select `Add Table` to get a dialog you will fill out like the one below.

![Add Lookup Table][add-lookup-table]
{: .figure }

1. For the type, choose `Ligature Substitution`
2. Under `Feature`, select `New` to add a new lookup table
3. From the dropdown, select `Standard Ligatures`
4. Select `OK` to create the table (I left the default name)

The interface shifts a little oddly when you click `New`, but don't worry. `liga` is the font feature that this type of substitution takes advantage of. While `Discretionary Ligatures (dlig)` may make more sense, I have had less success with making them work. If you need to go back to edit this at a later time, choose `Edit Metadata` with the lookup table selected.

![Ligature Lookup Table][lookup-table]
{: .preview }

## Step 2: Add the Ligatures

The actual ligatures are held in a lookup's subtables. To create a subtable.

1. Select the lookup table you just created
2. Click the `Add Subtable` button
3. Click `OK` (You can leave the default name)

FontForge will create the subtable and open it for editing.

![Subtable Entries][subtable-entries]

These are the entries you will create. The right column contains the combination of letters that form the ligature, separated by spaces. Letters are themselves, but some other characters would be spelled out, like `period(.)` for, you guessed it, the period. The left column contains the glyph to be substituted. To create the first entry:

1. Click `<New>` in the table
2. Enter `uniE400` in the left column
3. Enter `c a r r o t` in the right column

Repeat for `uniE401` and `h a p p y`.

Click `OK` to close out the subtable, and `OK` to close out of Font Information.

## Step 3: Test Your Ligatures

You can open up ametrics window to preview your font. Choose `Metrics > New Metrics Window` from the top menu.

![Ligature Metrics][metrics]
{: .preview }

Enter your ligature's component letters in the top text input. You should see the ligature glyph below.

## Step 4: Export your Font

When you're ready to generate your font:

1. Select `File > Generate Fonts&hellip;`
2. Choose `TrueType` as the font type (this is different than the previous exercises)
3. Make sure `Validate Before Saving` is unchecked
4. Select a location and name
5. Click `Generate`

Congratulations, you've got your font! Unfortunately, I was not able to get this font working out of the box and had to run it through FontSquirrel first. To do this:

1. Navigate to the FontSquirrel [Webfont Generator][font-squirrel-generator]
2. Upload your `.ttf` font file
3. Choose the `Expert&hellip;` export radio button
4. Under subsetting, choose `No subsetting` (this prevents FontSquirrel from cutting out your Private Use Area glyphs)
5. Download your kit

The resulting kit will contain your font in a bunch of different font formats. Pick whatever combination works best for you (you can also copy their `@font-face` rule if you'd like). To use ligatures, you will generally have to either turn on the CSS properties `text-rendering: optimizeLegibility` or `font-feature-settings: 'liga'` (with font-feature settings prefixed at the moment). For an example of how this might work, check out the [result demo][result].

[wikipedia-ligature]: http://en.wikipedia.org/wiki/Typographic_ligature
[exercise-01]: ../01-ascii
[exercise-02]: ../02-pua
[fontforge]: http://fontforge.github.io/
[open-sans]: http://www.google.com/fonts/specimen/Open+Sans
[repo]: https://github.com/betravis/icon-font-lab
[woff-support]: http://caniuse.com/#feat=woff
[font-squirrel-generator]: http://www.fontsquirrel
[bashburn]: http://thenounproject.com/bashburn
[issues]: https://github.com/betravis/icon-font-lab/issues
[twitter]: http://twitter.com/bear_travis
[result]: ../03-ligature-result

[carrot]: img/carrot.svg
[lookups]: img/lookups.png
[add-lookup-table]: img/add-lookup-table.png
[lookup-table]: img/lookup-table.png
[subtable-entries]: img/subtable-entries.png
[metrics]: img/metrics.png
