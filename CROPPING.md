If a film/scanner holder is visible in the scan, it will mess up the dust & scratch removal. An example of film holder being visible in a scan can be seen below.
The best way to prevent this is to just scan the negatives without a scan holder being visible (by cropping during the scanning process in your scanning software), but in some cases you might have a bunch of scans already done, and rescanning would be a hassle.

![ScanHolder](https://user-images.githubusercontent.com/67801159/149269398-69027f9b-a97b-491a-a138-9f81a8769db5.jpg)

Unfortunately both Preview and Affinity Photo delete any extra TIFF layers an image has when trying to crop it. This is a problem if you have infrared scans, and want to remove dust or scratches.

Currently the only way I've found to crop the TIFFs is by using Imagemagick. Here you will find instructions on how to do this.

### Instructions for Copping

1. Put a **copy** of the images you want to crop onto your desktop
	- The images will be modified directly, so make sure you have a **backup** of the originals!
2. Open the Terminal, and type in `cd desktop`
3. Type in `mogrify -gravity North -chop x500 image.tif` and hit enter
	- Change which direction (`North`) you want to chop off of the image from (`South`,  `East`, `West`)
	- Change the number (`x500`) to change how many pixels are being chopped off
	- Replace `image.tif` with the name of the file you want to crop
