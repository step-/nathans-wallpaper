# Changelog

## 20150503 (repository commit 20150606)

### Enhance usability

 * Add live preview. The desktop wallpaper is updated immediately as the
   file list selection changes. Changes are temporary and automatically
   revert on exit - unless the Apply button is clicked to set the current
   preview as the permanent desktop background.
 * Add BMP and TIFF image preview.
 * Add preview icons for folder and no-image objects.
 * Add application status bar.
 * Add tooltips to mode and action buttons and to preferences dialog.

### Enhance functionality

 * Add BMP, GIF and TIFF image rendering.
 * Add undistorted wallpaper stretching (constant aspect ratio).
 * Slideshow: add shuffle list, new image types. Reduce resource usage.
 * Redesigned preferences dialog with program chooser.
 * Extend command line options.

###  Miscellaneous

 * Version bump to 0.7.0.
 * Test on Fatdog64 701 gtkdialog 0.8.4, ROX-Filer only,
   [The Bitmap Test Suite 0.9](http://bmptestsuite.sourceforge.net/).
 * Set default Mode 'Centre'.
 * New localization strings (English only).
 * No longer are radio buttons sorted to place saved mode on top.
 * Fix broken preview when selecting some PNG images, no-images, and folders.
 * Fix action buttons firing twice on single toggle.
 * Fix Edit/View/Filer actions failing for wallpaper names with spaces.
 * Fix no-longer working gtkdialog3 version test (worked for 0.7.x only).
 * Change slideshow implementation when multiple command-line args are supplied.

###  Notes

 * Window icon set to gtk-select-color to improve cross-puppy compatibility.
 * Added folder `.preview`, which holds navigation previews (all as jpg).
 * Changed language detection code.
 * Refactored some code.
 * Undistorted wallpaper stretching extends the method that BK developed
   for Quirky to reshape a horizontal image (script `background_reshape`).
 * BK's script is here extended to add GIF and TIFF rendering, and
   vertical image cutting.  The latter allows filling the screen with any
   image aspect ratio.  This extended `background_reshape` script should be
   drop-in compatible with Quirky, but it's untested there.
 * Since `background_reshape` adds an image cache, the Clear button now
   extends to clear cached and preview images of the current selection. 
 * Script `set_bg` is modified to support other added features and fix
   some bugs.

###  Downgrading

To downgrade to version 0.6.3 uninstall the package, reboot, run once:

    /usr/local/apps/Wallpaper/set_bg /usr/share/backgrounds/default.jpg

### Command line quick help

 * Setting wallpaper from script in ~/Startup:

    /usr/bin/wallpaper ARG, where ARG can be:
    "/path/to/wallpaper.jpg"            # or other supported image format
    -about
    -nextslide path.ext                 # show path.ext (untested in 20150503 update)
    -play                               # show /usr/share/backgrounds/*
    path1.ext path2.ext [path.ext...]   # show path*.ext

### By file

**usr/local/apps/Wallpaper/folder.jpg and no-image.jpg**

Image sources:

 * http://www.caritasfreetown.org:81/images/open_icon_library-full/icons/png/256x256/places/oxygen-style/folder.png
 * http://commons.wikimedia.org/wiki/Category:Tango_project/mimetypes

     File-Image-x-generic_-_black.svg
     http://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Image-x-generic_-_black.svg/240px-Image-x-generic_-_black.svg.png
 * http://commons.wikimedia.org/wiki/Category:Tango_project/status

     Dialog-error.svg
     http://upload.wikimedia.org/wikipedia/commons/thumb/7/7f/Dialog-error.svg/48px-Dialog-error.svg.png

**usr/local/apps/Wallpaper/background_reshape**

 * Add image up/down scaling method if `pamscale` and `pamcomp` are installed.
 * Add horizontal cutting method, which together with vertical cutting method
   is the fall back path for image up-scaling when pamscale isn't installed.
 * Add GIF and TIFF support (when conversion utility is installed).
 * Prefix aspect-ratio subdirs with dot so they're invisible in browser dialog.
 * Don't dup `$1` in `/usr/share/backgrounds` 20150520
 * Fix `$1` not a file.  Fix empty image file. Fix unquoted pathnames.
 * Use: shorter pipes; `$(())` instead of `expr`, `$HOME` instead of `/root`.
 * By default `/tmp/backg.log` is disabled.
 * Refactor some code.
 * Change shebang from ash to dash.
 * Test on Fatdog64 701.

**usr/local/apps/Wallpaper/functions**

 * Allow spaces in pathnames.
 * Fix lost preferences when clicking [x] in title bar.
 * Add random slideshow setting.
 * Change shebang from sh to dash.
 * Change language detection code.
 * New/changed localization strings (English only).
 * New function programchooser() to fix `/usr/bin/programchooser` not installed.
 * Fix: no window icons [>forum](http://www.murga-linux.com/puppy/viewtopic.php?p=847169).
   _Fix could be Fatdog specific and it might not work on other puppies._

**usr/local/apps/Wallpaper/set_bg**

 * Merge mods from Quirky's `set_bg`.
 * Set default MODE='Centre'.
 * Expand -clear to remove wallpaper preview from folder `.preview` and
   stretched wallpaper from cache folders.
 * Add Windows BMP image type support.
 * Process prefix `mode':'` in image file path argument.
 * Change shebang from sh to dash, see [1](http://bkhome.org/blog/?viewDetailed=00554), [2](http://unix.stackexchange.com/questions/148035).
 * Fix: input image path with embedded `&` fails.
 * Fix: fails on some unquoted pathnames.
 * Put `background_reshape` in `$APPDIR` folder vs. Quirky's `/usr/sbin`.
 * Simplify some code. Test on Fatdog64 701.

**usr/local/apps/Wallpaper/slideshow**

 * Add option `-start-list`.
 * Allow `$2` as actual dir path.
 * Process prefix `mode':'` in image dir path argument.
 * Allow spaces in pathnames.
 * Change shebang from sh to dash.
 * Add and export `$APPDIR`.

**usr/bin/wallpaper**

 * Invoke `AppRun` with relative path.

**usr/bin/wallslide**

 * Add new supported image types.
 * Add random slideshow.
 * Add `$1` as image list file.
 * Allow spaces in pathnames.
 * Restrict search to files only.
 * Add default delay 15 seconds.
 * Replace command `wallpaper`.
 * Process prefix `mode':'` in image file dir argument.
 * Change shebang from sh to dash.

### Screenshots

Left: Forked version - Right: original version 0.6.3 (Fatdog64-700).

**Main window**

![main window](main-window.png)

**Options dialog**

![options dialog](options-dialog.png)

**Program chooser**

(not available in version 0.6.3)

![program chooser](program-chooser.png)
