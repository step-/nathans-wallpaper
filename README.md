# nathans-wallpaper
Bugfix and new functionality fork of Nathan's Wallpaper Setter for Fatdog64 linux (and Puppy linux flavors).

## Motivation
In 2006 Puppy linux forum user Nathan developed a shell-based wallpaper setter for Grafpup and stopped development at version 0.5.6 [http://www.murga-linux.com/puppy/viewtopic.php?t=69658](>forum thread). The app was hacked by various forum users and became version 0.6, which is still distributed with Fatdog64-700, a 64-bit OS in the Puppy linux family.

When I noticed that the Fatdog64 wallpaper setter had distorted my wallpaper, I started researching about this problem and found an [http://bkhome.org/blog/?viewDetailed=02377](old post) on Barry Kauler's blog that hinted at a possible solution. This solution was implemented in `pwallpaper` setter for Quirky, another OS of the Puppy family, but had never been integrated into Nathan's wallpaper setter. So I set out to integrate it for Fatdog64. And while doing that I fixed several other bugs (or creeping incompatibilities) and added considerable new functionality.

I tried to implement my code in a way that is compatible with Quirky's `pwallpaper` setter, and possibly with other recent Puppies that are still using, or want to use, Nathan's wallpaper setter. However, I make no promise about compatibility, as I develop and test on Fatdog64, and I have no time to test and fix other Puppies. For those I will be glad to merge pull-requests from other contributors.

One more thing to say about compatibility concerns Fatdog64 only. As mentioned, Fatdog has (Nathan's) wallpaper setter 0.6, which can run a slideshow. It also has another slideshow script, `/usr/bin/wallpaper-slideshow`. I have not even checked whether my fork of wallpaper setter 0.6 should be compatible with `wallpaper-slideshow`.

For now the version of wallpaper setter in this repo is Fatdog64-700's original version 0.6. I will start uploading my changes in a few days.

