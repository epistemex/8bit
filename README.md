8-bit
=====

**This project is frozen and won't be developed further, considering its experimental nature and level of interest. It's kept here for reference. Feel free to fork it if you want to continue the project.**

**Also see license information at the bottom of this page.**

---

8-bit inspired HTML5 Canvas that allow you to draw palette based, non-aliased graphics.

Basically built from scratch using low-level methods to get that authentic
retro look from pixelated lines, palette based colors to image dithering 
and more.

Quickly build classic retro-styled games, sprite editors, 8-bit looking
graphics for your web page, drawing applications and so forth.


Features
--------

- Retro feel guaranteed!
- Free of anti-aliasing and smoothness!
- All methods are 100% argument compatible with regular 2D canvas
- All properties are 100% name compatible with regular 2D canvas
- Supports transformations
- Supports patterns
- Supports gradients
- Supports compositing modes
- Supports images (dithered and reduced to current palette)
- Dithering includes Floyd-Steinberg, Sierra and ordered.
- Converts client mouse positions to scale via event listeners
- Support new canvas features such as `imageSmoothingEnabled`, `imageSmoothingQuality`, `ellipse()`, `currentTransform()`, +++
- *(N/A) Supports text and bitmap fonts*
- Supports chainable methods
- Supports optional convenience methods (`line()`, `circle()`, `clear()`, and more) by disabling strict mode.
- Bundled with a ton (well, 35) of retro palettes based on actual retro-machines as well as some game specific palettes, incl. but not limited to C64, VIC20, Amstrad, ZX Spectrum, Atari, Mac, MSX, EGA, PacMan, +++
- *(N/A) Loads and bit-crushes audio files incl. low-pass filter and frequency reduction*

Includes separate 8-bit Image object to load and dither image on-the fly (you can still use regular Image objects).

Includes polyfills for regular 2D context to enable support for ellipse() etc. 

**Random image loaded and drawn**:

![https://i.imgur.com/msrnmzw.png](https://i.imgur.com/msrnmzw.png)

**Some test shapes to check even-odd fill mode composited on top**:

![https://i.imgur.com/uyuWAqc.png](https://i.imgur.com/uyuWAqc.png)


Brief History
-------------

8-bit started out as retro-canvas a few years back. The original retro context
was rooted in more or less the old method of setting things like colors using
background color, foreground color, and also had its own method names and 
so forth. It was an experiment at the time to produce in particular
non-aliased vector graphics (lines, paths etc.) and had indexed palette
and dithering added to it as it went on.

It was later decided to scrap the first model and build a context that would
be 100% compatible with the 2D context, argument wise, so you could actually
run existing code just replacing the context type. The difference of course
being that the result would look and feel like retro, or 8-bit if you will.
It got rebuilt from scratch as a weekend-project with new strategies involved
such as using existing composition mechanisms to enhance capabilities and
performance. 

It's still an experiment though, and currently it has only implemented the needed
internal pieces without any particular optimizations. Depending on the interest 
the project may get allocated more resources and time to grow into something
useful for perhaps games etc. but its main purpose is for it to be used
as a building block in generating tools that can easily generate 8-bit
graphics. Or at least, that is what it's most realistically capable of at
the moment as running full games with lots of action is probably gonna be 
too much considering it's using JavaScript to process the data at multiple
stages. But never say never... it can run simpler things pretty well due to
the low resolution implied.

Install
-------

**8bit** can be installed in various ways:

- Git using HTTPS: `git clone https://github.com/epistemex/8bit.git`
- Git using SSH: `git clone git@github.com:epistemex/8bit.git`

No tape-loader, sorry!


Usage
-----

To use the canvas simply create an instance and knock yourselves out! The methods and properties
are the same as with 2D canvas, but using palette and low resolution instead.

    var canvas = document.getElementById("myCanvasElement");
    var ctx = canvas.getContext("8-bit");
    ...

**(N/A:)** For audio, simply load the audio file using the audio loader. 
The loaded audio is then handed over and brings back the good old crunchy
"HIFI" of the past to your speakers.

More info coming later - star and follow to keep yourself updated!


Notes
-----

Although the calls are identical as to the ordinary 2D context, it does come
with some constraints due to either performance or other reasons such as
need for access to internal workings. For these reasons the following
object works only with the 8-bit context:

**These objects exist due to the need pre-processing and palette dithering:**

- _8bit.Image
- _8bit.Pattern
- _8bit.Gradient

You *can* use regular images (and video etc.) with the drawImage() method,
but it will require the image source to be dithered on the fly which takes
a higher performance-hit than using the _8bit.Image instance.

For patterns and gradients you won't notice much difference than with 2D
context as you will use the createPattern() and create*Gradient() methods.
You operate with them in the same way as before, but they are not 
interchangeable with ordinary 2D equivalent objects.

**These exist due to need for deep access (path data) and compatibility (matrix):**

- _8bit.Path2D
- _8bit.Matrix

There are others as well, but they are marked as private.


Known Issues left as-is
-----------------------

- Non-zero winding not implemented (use "evenodd" fill mode)
- No text methods implemented
- No line-formatting implemented (join, cap, width etc.)
- In need of a ton of optimizations for image dithering, polygon fill etc.
- Not all features are documented. Refer to regular [2D context documentation](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D) as well as the included Quick Setup (see docs) for general usage.


License
-------

![CC](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)<br>This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/)


*&copy; Epistemex 2013-2017, 2024*
 
![Epistemex](https://i.imgur.com/wZSsyt8.png)
