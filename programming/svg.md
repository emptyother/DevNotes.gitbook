---
description: Dealing with Scalable Vector Graphic files.
---

# SVG

## Preview SVG in Windows

To preview SVG in Windows thumbnails, [download this plugin](https://archive.codeplex.com/?p=svgextension).

**Source**: [https://superuser.com/questions/342052/](https://superuser.com/questions/342052/)

## Editing SVGs

### Inkscape

Desktop app.

[https://inkscape.org/en/](https://inkscape.org/en/)

### SVG-edit

Web app. Not many features.

[https://svg-edit.github.io/svgedit/releases/svg-edit-2.8.1/svg-editor.html](https://svg-edit.github.io/svgedit/releases/svg-edit-2.8.1/svg-editor.html)

## Optimizing SVGs

The images is already optimized by ember-inline-svg using the svgo package, but if you want to do it manually \(or need to clean up messy SVG code\) heres an online implementation of svgo:

[https://jakearchibald.github.io/svgomg/](https://jakearchibald.github.io/svgomg/)

### Beware ⚠

If you use SVGOMG, do not use the "Round/rewrite paths/numbers/transforms". This will make it difficult to open the svg file in editors. This is because SVGOMG changes numbers like 0.14 to .14. This makes a variable like "1.12 0.14" become shortened to "1.12.14". Browsers read this just fine, but editors dont.

Manual fix is to go trough the entire paths and manually adding 0 in front of dots you THINK has been shortened. Keep a preview open to see when you mess it up.

## SVG Paths

Useful knowledge when trying to fix SVGs. Paths have a property named "d" that renders the path. In that property, each letter is a "line command", and every preceeding number is a parameter. A big-cased letter is a absolute path, a small-case letter is a relative path. The first two parameters are usually x and y, but the parameters can be shortened.

Line commands for paths:

| Command | Description |
| :--- | :--- |
| M | Moves the cursor to a position |
| Z | Closes the path \(draws a line straight to the first position\) |
| L | Line to \(draws a line from the current to a new position\) |
| H | Horizontal line \(no y position\) |
| V | Vertical line \(no x position\) |
| C | Curves |
| S | Multiple curves |
| Q | Simpler curve |
| T | Simpler multiple curves |
| A | Arcs |

