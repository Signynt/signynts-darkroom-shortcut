Unfortunately both Preview and Affinity Photo delete any extra TIFF layers an image has when trying to crop it. This is a problem if you have infrared scans, and want to remove dust or scratches.
The best way to do things it just to scan the images without a scan holder being visible, but in some cases you might have a bunch of scans already done, and rescanning would be a hassle.

Currently the only way I've found to crop the TIFFs is by using Imagemagick. Here you will find instructions on how to do this.

### Instructions for Copping

1. Put a **copy** of the images you want to crop onto your desktop
	- The images will be modified directly, so make sure you have a **backup** of the originals!
2. Open the Terminal, and type in `cd desktop`
3. Type in `mogrify -gravity North -chop x500 image.tif` and hit enter
	- Change which direction (`North`) you want to chop off of the image from (`South`,  `East`, `West`)
	- Change the number (`x500`) to change how many pixels are being chopped off
	- Replace `image.tif` with the name of the file you want to crop
