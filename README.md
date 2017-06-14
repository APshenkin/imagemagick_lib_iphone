## Compiled downloads

You can grab the latest compiled ImageMagick from releases

## Compiling ImageMagick and IMDelegates

The directory structure has to be:

```
./build/ImageMagick-VERSION/       <- ImageMagick top directory
./build/IMDelegates/               <- Some delegates: jpeg + png + tiff
./build/IMDelegates/jpeg-9b/       <- jpeg lib
./build/IMDelegates/libpng-1.6.28  <- png lib
./build/IMDelegates/tiff-4.0.4     <- tiff lib
```

If you don't have this directory structure you can either create it or try
change around the script. You can find the delegate libraries on the <a
href="ftp://ftp.imagemagick.org/pub/ImageMagick/delegates/">ImageMagick ftp</a>
or on the respective websites.

The main script to run is:

```./all.sh VERSION|clean``` where VERSION is the version of ImageMagick
you want to compile (e.g., 6.8.9-10), if 'clean' is passed, the script will
clean all the log files and the directories it created.

Upon successful compilation a folder called "IMPORT_ME" will be created from
where you start the script: you can import it into your XCode project.

The rest of the scripts are invoked by all.sh and offer the following:

```./env.sh``` sets up environment variables used by the other scripts.
This is most probably the script you want to modify to suit your needs (e.g.,
set up which architectures will be compiles, verbosity level, ...)

```./flags.sh``` saves, sets up and restores compiler-related values

```./utils.sh``` offers some functions used in the other scripts

```./compile_*.sh``` are the scripts used to compile the respective component

To compile tiff, read comments from all.sh script

## XCode project settings

After including everything into XCode please also make sure to have these settings (Build tab of the project information):

* Other Linker Flags: -lMagickCore -lMagickWand -lz -lbz2 -ljpeg -lpng (-ltiff if you compile with tiff)
* Header Search Paths: $(SRCROOT) - make it Recursive
* Library Search Paths: $(SRCROOT) - make it Recursive

## Sample project

A more or less updated project is found in the IM_Test subfolder
