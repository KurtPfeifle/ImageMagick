### Prerequisites

<!-- The more checkmarks you can set below, the higher your chance that this issue can be looked into fast:-->

- [ ] I have written a descriptive issue title
- [ ] I have checked: this issue is specific to the AppImage version of ImageMagick; it does not occur with a "standard" installed package (.rpm, .deb, ...)
- [ ] I have verified that I am using the latest version of ImageMagick (`magick convert -version`)
- [ ] I have searched [open](https://github.com/ImageMagick/ImageMagick/issues) and [closed ImageMagick](https://github.com/ImageMagick/ImageMagick/issues?q=is%3Aissue+is%3Aclosed) issues. I am sure it has not already been reported
- [ ] I have searched [open](https://github.com/KurtPfeifle/ImageMagick/issues) and [closed AppImage/ImageMagick](https://github.com/KurtPfeifle/ImageMagick/issues?q=is%3Aissue+is%3Aclosed) issues. I am sure it has not already been reported

### Description
<!-- A description of the bug or feature -->

### Steps to Reproduce
<!-- List of steps, sample code, failing test or link to a project that reproduces the behavior.
     Make sure you place a stack trace inside a code (```) block to avoid linking unrelated issues -->

### System Configuration
<!-- Tell us about the environment where you are experiencing the bug -->

**ImageMagick version:**

- Output of *`imagemagick-*.AppImage convert -version`*,  
  or, if you use a symlink or a re-named AppImage: *`name convert -version`*
    
- Output of *`imagemagick-*.AppImage -list configure`*,  
  or, if you use a symlink or a re-named AppImage: *`name convert -list configure`*

**Environment** (operating system, version and so on):

- Output of *`cat /etc/*release`*
    
- Output of *`cat /etc/*version`*
    
- Output of *`uname -a`*

**AppImage Configuration:**

- Output of *`imagemagick-*.AppImage --appimage-version`*,  
  or, if you use a symlink or a re-named AppImage: *`name --appimage-version`*

**Additional information:**

<!-- Thanks for reporting the issue to ImageMagick/AppImage! -->
