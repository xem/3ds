# Hello Screens, VRAM and framebuffers!

In a previous chapter, we talked about framebuffers. We will now see what this means.
<br>The 3DS VRAM (video memory) holds the image information of three screens:

- The top-left screen (the image sent to your left eye in stereoscopic (3D) mode; also used in 2D mode).
- The top-right screen (the image sent to your right eye in stereoscopic mode; unused in 2D mode).
- The bottom screen (2D only)

For each screen, there is room in the VRAM for two images, called "framebuffers", of "fb0 / fb1" for short.
<br>The two framebuffers replace each other at each frame (60 times per second):
- when fb 0 is displayed on a screen, fb1 is pre-rendered for the next frame.
- on the next frame, fb0 is reset, fb1 is displayed on screen and fb0 is pre-rendered for next frame.
- on the next frame, fb1 is reset, fb0 is displayed on screen and fb1 is pre-rendered for next frame.

etc, etc...
<br>
to vulgarize, let's just say that the 3DS does this under the hood, at each frame and for each screen, while your code puts the ink on the next paper :)

<img src="http://i1238.photobucket.com/albums/ff492/machineking0011/1235471162_duckrabbitseason.gif">

That's why we flush (reset) and swap the buffers at the end of the main loop. It allows the homebrew's code to always draw the next frame without risking to alter what is currently on screen.

In the VRAM, framebuffers store the color information of each pixel of the screen.
<br>Each pixel color is a mix of Red, Green and Blue (the primary colors for screens).
<br>Each primary color is stored on one byte (its value goes from 0 to 255).
<br>Top screens' framebuffers take 400 x 240 x 3 bytes, and the bottom screen's framebuffers take 320 x 240 x 3 bytes.

But it's not that simple:
- By default, the pixels colors are stored in reverse order (B,G,R instead of R,G,B).
- In the VRAM, all the screens are rotated by -90 degrees, as if you turned your 3DS to look at it from the right side.

To sum up, on each screen, both framebuffers use 3 bytes to store Blue, Green and Red components of each pixel, starting from the bottom-left pixel and going through each column from bottom to top until it reaches the top-right pixel.