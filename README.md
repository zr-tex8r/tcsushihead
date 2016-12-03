tcsushihead
===========

LaTeX: to place a sushi flow in the page headers

If you don't see what it means, just try it.

### SYSTEM REQUIREMENT

  * TeX format: LaTeX.
  * TeX engine: pdfTeX, XeTeX, LuaTeX, and any DVI-output engines.
  * DVI-ware (in DVI-output mode): dvipdfmx.
  * Required packages:
      - animate
      - bxcoloremoji

The [bxcoloremoji package] is needed because the tcsushihead package
uses the sushi image file (emoji_images/twemoji-pdf/1F363.pdf) provided
by bxcoloremoji.

[bxcoloremoji package]: https://github.com/zr-tex8r/BXcoloremoji

### INSTALLATION

  - `*.sty` → $TEXMF/tex/latex/tcsushihead

### LICENSE

This package is distributed under the MIT license.

### PACKAGE LOADING

    \usepackage[option,...]{tcsushihead}

The following options are available:

  * `dvipdfmx`: Specifies that dvipdfmx should be used.
  * `default=true|false`: Whether the default page style should be set to
    `sushihead`. The default value is `true`. If `default=false` is given,
    then the page style will be left unchanged. You can still change the
    page style by invoking `\pagestyle{sushihead}`.
  * Any key-value setting valid for `\sushiheadsetup`.

### USAGE

When this package is loaded (without `default=false` option), then the
default page style is set to `sushihead`, in which style, the footer is
empty and the header is the animation of flowing sushi. The animation
line consists of infinite alternation of runs of sushi and gaps. By
default, the length of a sushi run is equal to the current page number.

NOTE: The animation inside PDF documents is supported by very few PDF
viewers, including Adobe Reader.

Moreover, some user commands are available.

  * `\sushiheadsetup{KEY=VALUE,...}`: Configures sushi flow animation.
      - `count=<number>`: The number of sushi images in a run. The valid
        range is 0 to 100, where 0 means that the current page number
        should be used. In any case, the value exceeding 100 is capped.
      - `size=<length>`: The size of a sushi image.
      - `gap=<length>`: The amount of gaps between sushi runs.
      - `cycle=<real>`: The duration of an animation cycle, in seconds.
        Its value must be 0.1 or greater.
      - `ticks=<number>`: The number of frames in an animation cycle.
        When the frame rate (derived from `cycle` and `ticks`) exceeds
        100/s, the value is capped. (Probably the performance limit of
        Adobe Reader is much lower.)
      - `file=<path>`: The path of the image file that is used instead of
        the standard one.
      - `bb=<bbox>`: The bounding box (`bb` value of `\includegraphics`)
        of the image specified by `file`. The value is used only by
        `dvipdfmx` driver, and is necessary only when the auto-execution
        of extractbb is not available.

  * `\ShowSushiBar{<length>}`: Puts an animaton line of the given length
    right there.

REVISION HISTORY
----------------

  * Version 0.2  ‹2016/12/03›
      - First public version.

--------------------
Takayuki YATO (aka. "ZR")  
Twitter: @zr_tex8r
