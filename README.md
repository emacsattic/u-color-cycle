# u-color-cycle.el

## Introduction

u-color-cycle provides a set of commands which temporarily change the
colors in the current buffer.  Colors will change until the next
interaction (key press, mouse event) occurs.  The original color-status
of the current buffer is restored afterwards.  The contents of the
buffer are unchanged! Load this file and say `M-x u-color-cycle-window
RET` to find out what this means.

The following color-cycling methods are available:

* `u-color-cycle-window`:
    The whole text gets the same foreground color which is for changed
    smoothly.
* `u-color-cycle-window-rainbow`:
    The text color changes smoothly from one character to the next.
    The colors move through the text.  This method was contributed by
    Jesse Weinstein.
* `u-color-cycle-window-fade`:
    The foreground colors slowly fade away so that the buffer contents
    become "invisible".
* `u-color-cycle-window-swap`:
    The faces (not only colors) in the buffer are interchanged between
    text portions with different faces.

Each command exists in a `u-color-cycle-region-*` variant as well.

You may want to add the u-color-cycle functions to the list of
`zone-programs`. This is one way to do it:

    (eval-after-load 'zone 
      '(progn 
         (load-library "u-color-cycle") 
         (setq zone-programs (vconcat zone-programs [u-color-cycle-window
                                      u-color-cycle-window-fade
                                      u-color-cycle-window-swap
                                      u-color-cycle-window-rainbow]))))

u-color-cycle uses overlays.  It might therefore happen that
interferences with other packages like highlight-current-line or hifill
occur.


The overlay stuff was inspired by flyspell.el


## History

* Version 2.1
  *  Fixed compatibility issues with Emacs 21 and 22.

* Version 2.0
  *  Modified by Jesse Weinstein <jessw@netwood.net> on 6/8/2004 to
     display different colors on each character, in a rainbow pattern.
  *  Added color-cycling-swap and color-cycling-fade.
  *  Tested with Emacs 21.3.

* Version -
  *  Initial release.
  *  Tested with Emacs 20.x and XEmacs 21.1.x.
