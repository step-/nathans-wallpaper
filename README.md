# nathans-wallpaper

Bugfix and new functionality fork of Nathan's Wallpaper Setter for Fatdog64 linux (and Puppy linux flavors).

## Motivation

In 2006 Puppy linux forum user Nathan developed a shell-based wallpaper setter for Grafpup and stopped development at version 0.5.6 [>forum thread](http://www.murga-linux.com/puppy/viewtopic.php?t=69658). The app was hacked by various forum users and became version 0.6, which is still distributed with Fatdog64-700, a 64-bit OS in the Puppy linux family.

When I noticed that the Fatdog64 wallpaper setter had distorted my wallpaper, I started researching about this problem and found an [old post](http://bkhome.org/blog/?viewDetailed=02377) on Barry Kauler's blog that hinted at a possible solution. This solution was implemented in `pwallpaper` setter for Quirky, another OS of the Puppy family, but had never been integrated into Nathan's wallpaper setter. So I set out to integrate it for Fatdog64. And while doing that I fixed several other bugs (or creeping incompatibilities) and added considerable new functionality.

## Overview

Wallpaper setter 0.7.0 enhances usability and functionality:

 * New live preview mode - The desktop wallpaper is updated immediately as the
   file list selection changes. Changes are temporary and automatically
   revert on exit, or can be made permanent.
 * Full BMP, GIF and TIFF support across all program functions.
 * Preview icons for folder and no-image objects.
 * New application status bar displays image meta data.
 * Tooltips added to mode and action buttons and to preferences dialog.
 * Undistorted wallpaper stretching (constant aspect ratio).
 * Slideshow: add shuffle list, new image types, lower resource usage.
 * Redesigned preferences dialog with program chooser.
 * Bug and incompatibility fixes.
 * Test on Fatdog64 701, gtkdialog 0.8.4.
 * See full set of changes in [Changelog](Changelog.md) file.

## Starting, command line, slideshow

Normally you should start the Wallpaper setter GUI from Fatdog64's Control
Panel, but a command line is also available:

    /usr/bin/wallpaper [ARG]            # where ARG can be:
    "/path/to/wallpaper.jpg"            # set background (JPEG, PNG, etc.)
    -about                              # display version dialog and exit
    -play[=mode]                        # play images under slideshow directory
    -play-list=playlist-file            # play image paths in playlist-file
    path1.ext path2.ext [path.ext...]   # play path*.ext
    -stop                               # stop slideshow

Note that 'Live mode' is only available when no ARG is specified. In this case you can play a slideshow by selecting "Play" from the application menu.

The slideshow directory is set in the Preferences dialog (application menu).
The slideshow plays using the current wallpaper mode (Centre, Tile, Scale
or Stretch). You can specify a different mode in the `-play` option or by
prepending the mode and a colon to the image path argument, i.e.,

    /usr/bin/wallpaper Stretch:/path/to/wallpaper.jpg

A playlist-file simply lists the set of image filepaths, one per line,
formatted as `[mode':']/path/to/image.ext` like in the previous example.

To set slideshow delay and shuffle mode use the Preferences dialog (application
menu) or manually set suitable values in `$HOME/.config/wallpaper/preferences`.

## Compatibility

I tried to implement my code in a way that is compatible with Quirky's `pwallpaper` setter, and possibly with other recent Puppies that are still using, or want to use, Nathan's wallpaper setter. However, I make no promise about compatibility, as I develop and test on Fatdog64, and I have no time to test and fix other Puppies. For those I will be glad to merge pull-requests from other contributors.

One more thing to say about compatibility concerns Fatdog64 only. As mentioned, Fatdog has (Nathan's) wallpaper setter 0.6.3, which can run a slideshow. It also has another slideshow script, `/usr/bin/wallpaper-slideshow`. I have not even checked whether my fork of wallpaper setter 0.6.3 should be compatible with `wallpaper-slideshow`.

## Bugs

Please file bugs in the Issues section of the github [repository](https://github.com/step-/nathans-wallpaper/issues).

## Screenshots

Left: Forked version - Right: original version 0.6.3 (Fatdog64-700).

**Main window**

![main window](main-window.png)

**Options dialog**

![options dialog](options-dialog.png)

**Program chooser**

(not available in version 0.6.3)

![program chooser](program-chooser.png)

