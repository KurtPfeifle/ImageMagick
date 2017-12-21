# First *`ImageMagick`* AppImage

This is my first shot at building an AppImage for *ImageMagick v7* which sports a *custom AppRun*. The AppRun is implemented as a shell script.

The AppImage currently gives you this version of ImageMagick v7:

```
$~>  ./ImageMagick-xperimental.AppImage  -version

   Version: ImageMagick 7.0.7-15 Q16 x86_64 20171208 http://www.imagemagick.org
   Copyright: © 1999-2018 ImageMagick Studio LLC
   License: http://www.imagemagick.org/script/license.php
   Features: Cipher DPC HDRI OpenMP 
   Delegates (built-in): bzlib cairo djvu fftw fontconfig freetype gvc jbig jng jp2 jpeg lcms lqr lzma openexr pangocairo png raw rsvg tiff wmf x xml zlib
```

If you are an ImageMagick user already, you also must feel comfortable to have left GUI, mouse and touchpad behind, right? Intimate familiarity with all kinds of CLI tools can be assumed?

My main reason for building this AppImage is: I want to have an easy access to the latest "bleeding edge" releases of ImageMagick (which happen every fortnight or so), without the need to re-compile the code every few days and for each Linux system I use.

Also this AppImage's features expand a bit beyond the standard AppImage philosophy (*"One App == One File"*): it provides *multiple apps inside one AppImage file*. It also carries all the current documentation files (manual pages, HTML documents) inside and makes them accessible to AppImage users.

Hence you should prepare your environment for conveniently accessing the main ImageMagick CLI utility, *`magick`*,  embedded in the AppImage:

     $~>  mkdir $HOME/AppImages
     $~>  cd $HOME/AppImages
     $~>  wget $URL-of-AppImage
     $~>  mkdir $HOME/bin
     $~>  cd $HOME/bin
     $~>  ln -s ../AppImages/ImageMagick-x86_64.AppImage magick
     $~>  export PATH=$HOME/bin:$PATH

Of course, you can choose to not do that. But then you have to deal with typing the long original name of this AppImage, *`./ImageMagick-xperimental.AppImage`*, every time you want to run it...

You are also free to rename the whole thing after you downloaded it. You can even simply use *`im`* as the name. 
<sup>(It is little known, but very convenient, that AppImages do not require to carry the filename suffix of *`.AppImage`* in order to work.)</sup>

## What's new in ImageMagick v7?

ImageMagick v6 had its rich functionalities distributed across a small set of individual utilities: *`animate`*, *`compare`*,  *`composite`*,  *`conjure`*,  *`convert`*,  *`display`*,  *`identify`*,  *`import`*,  *`magick`*,  *`magick-script`*,  *`mogrify`*,  *`montage`* and  *`stream`*.

With ImageMagick v6 this changed: it's all in *`magick`* now, and you can get the exactly same behaviour of former *`convert`* by running it as a sub-command for *`magick`*:

     $~>  magick convert

The same is true for the other commands:

     $~>  magick convert
     $~>  magick identify
     $~>  magick compare
     $~>  magick montage
     $~>  magick display
     $~>  magick mogrify
     $~>  magick import
     $~>  magick stream
     $~>  magick animate
     $~>  magick magick-script

## Custom *AppRun*

The AppImage comes with a custom AppRun providing additional help. Try to run it with *`ImageMagick-xperimental.AppImage help`* first. Then walk from there, and try:

    $~>  ImageMagick-xperimental.AppImage listman         # List all embedded manual pages
    $~>  ImageMagick-xperimental.AppImage man compare     # View the manual page for 'compare'
    $~>  ImageMagick-xperimental.AppImage listhtml        # List all embedded HTML pages
    $~>  ImageMagick-xperimental.AppImage html fx.html    # View the 'fx.html' page
    $~>  [....]

![Help screen if AppImage is started with `--help` parameter.](https://user-images.githubusercontent.com/4747960/34114984-8b78173a-e414-11e7-8aa0-f05ea2a627db.jpg "Help screen if AppImage is started with `--help` parameter.")


Or, if you created the *`magick`*-symlink as described above:

    $~>  magick listman         # List all embedded manual pages
    $~>  magick man compare     # View the manual page for 'compare'
    $~>  magick listhtml        # List all embedded HTML pages
    $~>  magick html fx.html    # View the 'fx.html' page

![Help screen if symlink *"im"* pointing to real AppImage starts it.](https://user-images.githubusercontent.com/4747960/34114897-4e40b818-e414-11e7-94a7-2f8bf4138aaf.jpg  "Help screen if symlink *'im'* pointing to real AppImage starts it.")

## Updating this AppImage

There are various ways to update this AppImage. I recommend you do the following in order to get the benefits of the *binary delta block downloads* which saves bandwidth and time by only fetching those binary blocks of the AppImage which have changed in any new release:

    $~>   cd $HOME/bin
    $~>   wget https://github.com/AppImage/AppImageUpdate/releases/download/continuous/appimageupdatetool-180-d89753f-x86_64.AppImage
    $~>   mv appimageupdatetool-*-x86_64.AppImage aiu-tool
    $~>   chmod a+x aiu-tool

Now that this tool is in your $PATH, you can check for updates of this (or any other) AppImage from the command line:

    $~>  aiu-tool --help            # Display short help message
    $~>  aiu-tool any.AppImage      # Check for updates and do it, no questions asked

Be aware that for security reasons, the new + updated AppImage will not be executable by default. You have to run *`chmod +x`* on it before you can use it.

If you just want to *check* for updates, but not (yet) execute them, then:

    $~>  aiu-tool --check-for-update any.AppImage

Oh, and you can keep the AppImage update tool itself updated -- it can also update itself:

    $~>  aiu-tool --self-update

Or use any of the following:

    $~>  aiu-tool ./aiu-tool
    $~>  aiu-tool /path/to/appimageupdatetool-180-d89753f-x86_64.AppImage
    $~>  ./appimageupdatetool-180-d89753f-x86_64.AppImage ./appimageupdatetool-180-d89753f-x86_64.AppImage


