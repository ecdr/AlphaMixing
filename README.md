I'm doing some experiments with the SmartMatrix that requires transparency. That is, the ability of the background to be seen through pixels drawn over it, with the colors mixed accordingly. I looked through Louis' driver code and found it trivial to add alpha mixing at the lowest level. Only three files in the driver required changes and those changes are simple. The most important thing to know to use transparency is to understand the rgb24 has been extended to include a byte of alpha. A color with an alpha value of 255 is totally opaque; an alpha value of 0 is transparent. Colors with in between alpha values are semi transparent.

All of the changes to the driver code are listed in comments of the alpha mixing sketch attached. If you make these changes, the define USE_ALPHA_MIXING in SmartMatrix.h controls whether alpha mixing is utilized. If USE_ALPHA_MIXING equals 1, alpha mixing is used. If set to 0, alpha mixing is disabled.

The sketch itself creates a grid of red pixels and then divides the display into four quadrants, each with a different alpha value. When this sketch is run, you'll see the affect of differing alpha values. As the alpha value increases in the filled rectangles which draw over the quadrants the red pixels become less and less visible.

If you find a bug let me know.

Craig Lindley