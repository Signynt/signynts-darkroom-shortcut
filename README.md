> For a version that is entirely contained in Affinty Photo, see the old workflow [Signynt's Darkroom Macro](https://github.com/Signynt/signynts-darkroom-macro)

# Signynt's Darkroom Shortcut
Signynt's Darkroom Shortcut constitutes a workflow for film negative inversion with dust and scratch removal. 
It consists of an Apple Workflow, three shell scripts that utilize Imagemagick (made by [Fred Weinhaus](http://www.fmwconcepts.com/imagemagick/index.php) and [Jaz99](https://www.flickr.com/people/jaz99)), and an Affinity Photo macro / Photoshop action if you would like to use the dust removal option.

Using this shortcut gives you quick access to high quality, neutral and ready to edit RAW images with just one click. It also optionally provides access to quick and high quality dust or scratch removal that is better than the scanning softwares automatic options.

It can be used with DSLR scans, scans made with Silverfast or VueScan, and supports both B&W as well as color negative film.

![Github](https://user-images.githubusercontent.com/67801159/146692420-04df4cdc-dab6-494f-b414-cc3563ee55f1.png)

## Installation
Please read the instructions carefully, and use the YouTube video if you have trouble understanging any of the steps. If you still are having trouble, open an [Issue](https://github.com/Signynt/signynts-darkroom-shortcut/issues/new/choose), or DM me on [Reddit](https://www.reddit.com/user/Signynt).

1. Install [Imagemagick](https://imagemagick.org):

The easiest way to do this is using [Brew](https://brew.sh).

If you don't yet have [Brew](https://brew.sh) installed, paste this command in to the Terminal:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once [Brew](https://brew.sh) is installed run these two commands in the Terminal to install [Imagemagick](https://imagemagick.org):
	
```
brew install imagemagick
```

Newer versions of imagemagick have unfortunately broken `negfix8`, so once you've installed it you'll need to switch to a previous version by running these 3 commands:

1. `brew install imagemagick@6`

2. `brew link --overwrite imagemagick@6`

3. `echo 'export PATH="/usr/local/opt/imagemagick@6/bin:$PATH"' >> ~/.zshrc`

You can now close the Terminal.

2. Download the latest [release](https://github.com/Signynt/signynts-darkroom-shortcut/archive/refs/tags/v1.6.zip) and open the zip file
3. Install the Apple Workflows that correspond to what kind of scans you are working with, and the software you use for scanning:
	- For black & white scans, install `Signynt's Darkroom Shortcut (B&W).workflow`
	- For color negative scans that were scanned without IR, install `Signynt's Darkroom Shortcut.workflow`
	- For color negative scans that were scanned with IR, install the workflow labeled with `(IR)` that corresponds to your scanning software
		- If you scan with Silverfast, install `Signynt's Darkroom Shortcut (IR) (Silverfast).workflow`
		- If you scan with VueScan, install `Signynt's Darkroom Shortcut (IR) (VueScan).workflow`
	- If you are DSLR scanning, open the folder called `DSLR Scanning` and install `Convert to TIFF.workflow`
4. Open the folder called `Macros` and install the dust removal macro for your image editing software
	- If you are using Affinity Photo, install `Signynt's Darkroom Shortcut.afmacros` by double clicking it
	- If you are using Photoshop, install `Signynt's Darkroom Shortcut.atn`
		1. Open a new Finder window and press `Cmd` + `Shift` + `G`
		2. Type in `/Library/Application Support/Adobe/Adobe Photoshop 2022/Presets/Actions` and hit enter to open your Photoshop Actions folder
		3. Move `Signynt's Darkroom Shortcut.atn` into the `Actions` folder
		4. Restart Photoshop
6. Install the scripts:

Open Finder and in the Menu Bar select `Go > Go to Folder` and type  `usr/local/bin`, then hit enter. This will open up the `bin` folder. 

Drag and drop the three scripts called `autocolor`, `autolevel` and `negfix8` from the `Scripts` folder to `bin`.

6. Enjoy! Test out the script on the [Example.tif](https://github.com/Signynt/signynts-darkroom-shortcut/releases/download/v1.1/Example.tif) file

If you have any trouble installing, try checking out my video tutorial to check if you are doing all the steps correctly.

> Important: If you get an error while trying to use the shortcut, one of the most common reasons this can be caused is a messed up `$PATH`. To fix this, open the Terminal and run this command: 
>```
>echo "export PATH=/opt/homebrew/bin:$PATH" >> ~/.zshrc
>```
> Close the Terminal and try the shortcut again, in most cases it will work now.

## How To Use
1. Scan a film negative as a RAW TIFF file, optionally select the infrared scan option
	- In Silverfast for example select `64 Bit HDRi RAW` as the scan option
2. Right click on the output file, hover over `Quick Actions`, then select your corresponding shortcut 
	- If you would like to process multiple files at once, simply select all the files you would like the invert, then right click
3. Wait for the shortcut to finish loading. While it is running you will see a cog in the Menu Bar spinning
4. Each processed image should now have a corresponding image labeled `-Inverted` at the end of the filename, and you're done! If you selected the IR option continue to the next step.
5. The parts of the image recognized as dust or scratches will appear as if they have been ereased. To fix these parts of the image open it in Affinity Photo or Photoshop
6. **For Affinity Photo**: In the macros folder called `Signynt's Darkroom Shortcut` select the macro called `Remove Dust`
	- You can check to see if you are happy with the infill by comparing the layer called `Dust Removed` with the layer called `Image`. 
	- To remove dust that was missed: Use `Inpainting Brush Tool`
	- To undo the dust removal in certain areas: Select the `Dust Removed` layer & use the `Erease Brush Tool` to erease those areas
6. **For Photoshop**: In the actions folder called `Signynt's Darkroom Shortcut` select the action called `Remove Dust` and press the play button
	- To remove dust that was missed: Use `Spot Healing Tool`
	- To undo the dust removal in certain areas: Use a `Layer Mask` & a brush set to black to paint over the areas
7. Edit the image to your liking and export it!

> Important: For the dust & scratch removal to work, no part of the film/scanner holder may be visible. For details, and instructions on how to properly crop this out, see [these instructions](https://github.com/Signynt/signynts-darkroom-shortcut/blob/f190a67ecfc8ff810f80ceacfb01857256e762ee/CROPPING.md).

### Use with DSLR Scans

The workflow requires input images to be TIFF files, however most DSLR cameras output other RAW formats, such as NEF, ARW or DNG. 
In those cases the images must first be converted to TIFF files, which can be done with the workflow which you will find in the `DSLR Scanning` folder (double click `Convert to TIFF.worflow` to install it). 

Before using the workflow as described above you must first follow these steps:

1. Select all you DSLR scans
2. Right click, hover over `Quick Actions`, then select `Convert to TIFF`

After running you will have a duplicate of each image which is a TIFF file, and is labeled as such. You can then select these and run them through the workflow as described above. Please note you can not use the IR version with DSLR scans.

> Important: Make sure you crop the image too remove any of the lighttable that might be visible in the image, otherwise you will run into errors!

## More Information

For more information on the plugin and how it works see my explaination video:

[![Signynt's Darkroom Shortcut Video](https://res.cloudinary.com/marcomontalbano/image/upload/v1639958293/video_to_markdown/images/youtube--Sv1BnDUgRBM-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/Sv1BnDUgRBM "Signynt's Darkroom Shortcut Video")

## Credit
This workflow uses Imagemagick scripts to work, which are responsible for the main steps of inversion and color correction. Full credit goes to the creators of these scripts.
- [negfix8](https://sites.google.com/site/negfix/howto) was created by [Jaz99](https://www.flickr.com/people/jaz99), thank you
- [autolevel](http://www.fmwconcepts.com/imagemagick/autolevel/index.php) and [autocolor](http://www.fmwconcepts.com/imagemagick/autocolor/index.php) were created by Fred Weinhaus, thank you 
- The Photoshop action was contributed by @gjauxfaux, thank you

### Licensing

Please note the licensing from [Fred Weinhaus](http://www.fmwconcepts.com/imagemagick/index.php), which apply to the [autolevel](http://www.fmwconcepts.com/imagemagick/autolevel/index.php) and [autocolor](http://www.fmwconcepts.com/imagemagick/autocolor/index.php) scripts:

> Licensing:
> Copyright © Fred Weinhaus
>
> My scripts are available free of charge for non-commercial (non-profit) use, ONLY.
> 
> For use of my scripts in commercial (for-profit) environments or non-free applications, please contact me (Fred Weinhaus) for licensing arrangements. My email address is fmw at alink dot net.
> 
> If you: 1) redistribute, 2) incorporate any of these scripts into other free applications or 3) reprogram them in another scripting language, then you must contact me for permission, especially if the result might be used in a commercial or for-profit environment.
>
> Usage, whether stated or not in the script, is restricted to the above licensing arrangements. It is also subject, in a subordinate manner, to the ImageMagick license, which can be found at: http://www.imagemagick.org/script/license.php
