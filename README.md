# imageresampler
Automatically exported from code.google.com/p/imageresampler

imageresampler is a pubic domain (see unlicense.org) C++ class for memory efficient image/bitmap resampling loosely based on a (heavily bugfixed) version of Dale Schumacher's public domain resampler in Graphics Gems 3 (1994). It supports a wide range of filter kernels and windowing functions, clamp/wrap/reflect boundary modes, arbitrary source image phase offsets, floating point pixels with any number of components, and can process images much larger than available memory.

A long time ago, this resampler was written originally in C and 16-bit x86 assembly and was used in a printer driver for a DOS image viewer product. Memory was extremely tight in this environment, which is why this class supports streaming resampling. I've also successfully used this class to generate texture mipmaps in the tool chains of various PC and console game projects. This version is written in fairly portable C++.

**Features**

- Can up/downsample completely independently on each axis.
- Plenty of antialiasing filters: box, tent, bell, b-spline, Mitchell, Lanczos 3/4/6/12, Blackman, Kaiser, Gaussian, etc.
- Filter kernels can be offset and scaled (shrinking the kernel a bit to sharpen the output is very useful when generating texture mipmaps)
- Supports clamp, wrap, etc. boundary modes - useful when filtering wrapping textures
- Chooses the axis resample order that minimizes the total number of ops, like Heckbert's Zoom.
- Operates on any number of input channels, floating point input/output
- Minimal memory/streaming operation: you feed it some input scanlines, and it gives you as many output scanlines as it can. Or if you don't care about RAM you can feed it all your input scanlines, then "pull" all the output scanlines.
- The source archive includes Visual C++ 2005 and 2008 solutions, and a Codeblocks 10.05 workspace.

**Release History**

- v2.21 - June 4, 2012: Added unlicense.org text (instead of just plain public domain), integrated GCC fixes supplied by Peter Nagy <petern@crytek.com>, Anteru at anteru.net, and clay@coge.net, added Codeblocks project (for testing with MinGW and GCC), added VS2008 project files, VS2008 static code analysis pass, added calls to delete at end of test.cpp.
- v2.20 - Dec. 31, 2008: Released to public domain on Google Code.
