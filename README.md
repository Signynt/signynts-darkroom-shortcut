# signynts-darkroom-shortcut
Signynt's Darkroom Shortcut constitutes a workflow for film negative inversion with dust or scratch removal. 
It consists of an Apple Workflow, three shell scripts that utilize Imagemagick, and an Affinity Photo macro if you would like to use the dust removal option.

Using this shortcut gives you quick access to high quality, neutral and ready to edit RAW images with just one click. It also optionally provides access to quick and high quality dust or scratch removal that is better than the scanning softwares automatic options.

## Installation
1. Install [Imagemagick](https://imagemagick.org):

The easiest way to do this is using [Brew](https://brew.sh).

If you don't yet have [Brew](https://brew.sh) installed, paste this command in to the Terminal:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once [Brew](https://brew.sh) is installed run these two commands in the Terminal to install [Imagemagick](https://imagemagick.org) with libtiff support:
```
brew install libtiff
```
	
```
brew install imagemagick
```
You can now close the Terminal.

2. Download the latest [release](https://github.com/Signynt/signynts-darkroom-shortcut/archive/refs/tags/v1.0.zip) and open the zip file
3. Install the two Apple Workflows called `Signynt's Darkroom Shortcut (IR).workflow` and `Signynt's Darkroom Shortcut.workflow` by double clicking on them
4. Install the Affinity Photo macro called `Signynt's Darkroom Shortcut v.1.0.afmacros` by double clicking on it
5. Install the scripts:

Open Finder and in the Menu Bar select `Go > Go to Folder` and type  `usr/local/bin`, then hit enter. This will open up the `bin` folder. 

Drag and drop the three scripts called `autocolor`, `autolevel` and `negfix8` from the `scripts` folder to `bin`.

6. Enjoy! Test out the script on the [Example.tif](https://github.com/Signynt/signynts-darkroom-shortcut/releases/download/v1.0/Example.tif) file

If you have any trouble installing, try checking out my video tutorial to check if you are doing all the steps correctly.

## How To Use
1. Scan a film negative as a RAW TIFF file, optionally select the infrared scan option
	- In Silverfast for example select `64 Bit HDRi RAW` as the scan option
2. Right click on the output file, hover over `Quick Actions`, then select one of the Shorcuts
	- If you used the infrared scan option and would like to remove any dust or scratches select `Signynt's Darkroom Shortcut (IR)`, if you didn't do an infrared scan or don't want the dust or scratches to be removed select `Signynt's Darkroom Shortcut`
	- If you would like to process multiple files at once, simply select all the files you would like the invert, then right click
3. Wait for the shortcut to finish loading. While it is running you will see a cog in the Menu Bar spinning
4. Each processed image should now have a corresponding image labeled `-Inverted` at the end of the filename, and you're done! If you selected the IR option continue to the next step.
5. The parts of the image recognized as dust or scratches will appear as if they have been ereased. To fix these parts of the image open it in Affinity Photo
6. In the macros folder called `Signynt's Darkroom Shortcut v.1.0` select the macro called `Remove Dust`
	- You can check to see if you are happy with the infill by comparing the layer called `Dust Removed` with the layer called `Image`. If you want to do the removal in a specific part of the image, erease the `Dust Removed` layer in that spot. If there is more dust that wasn't removed, you can select the `Inpainting Brush Tool` and remove them manually
7. Edit the image to your liking and export it!

## More Information

For more information on the plugin and how it works see my explaination video:

## Credit
This workflow uses Imagemagick scripts to work, which are responsible for the main steps of inversion and color correction. Full credit goes to the creators of these scripts.
- [negfix8](https://sites.google.com/site/negfix/howto) was created by [Jaz99](https://www.flickr.com/people/jaz99), thank you
- [autolevel](http://www.fmwconcepts.com/imagemagick/autolevel/index.php) and [autocolor](http://www.fmwconcepts.com/imagemagick/autocolor/index.php) were created by Fred Weinhaus, thank you 
