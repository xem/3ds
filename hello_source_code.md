# Hello source code!

Let's open source/main.c and analyse its contents:

````C
#include <3ds.h>

int main()
{
  // Initializations
  srvInit();        // services
  aptInit();        // applets
  hidInit(NULL);    // input
  gfxInit();        // graphics
  gfxSet3D(false);  // stereoscopy (true: enabled / false: disabled)
  u32 kDown;        // keys down
  u32 kHeld;        // keys pressed
  u32 kUp;          // keys up

  // Main loop
  while (aptMainLoop())
  {

    // Wait for next frame
    gspWaitForVBlank();

    // Read which buttons are currently pressed or not
    hidScanInput();
    kDown = hidKeysDown();
    kHeld = hidKeysHeld();
    kUp = hidKeysUp();

    // If START button is pressed, break loop and quit
    if (kDown & KEY_START){
      break;
    }


    /** Your code goes here **/


    // Flush and swap framebuffers
    gfxFlushBuffers();
    gfxSwapBuffers();
  }

  // Exit
  gfxExit();
  hidExit();
  aptExit();
  srvExit();

  // Return to hbmenu
  return 0;
}
````

That's the minimal homebrew you could imagine.

It's not very useful yet (it just runs until we press START to exit.), but it will be a lot better soon!

As you may have guessed, it does the following things:
- include 3ds.h (a library made to easily access 3DS's hardware with code).
- initialize various things (services, applets, inputs, graphics...). Homebrews could not do much without those.
- Start an infinite loop (each iteration represents a frame, and up to 60 frames are displayed per second.
- In each iteration:
  - Wait for the screen to be ready.
  - "Read" which buttons are currently pressed. If START is pressed, we quit the infinite loop.
  <br>(NB: pressing START is becoming the standard way to quit homebrews, but of course you can change this behavior),
  - Swap and flush current framebuffers (we'll explain that later).
- After the loop, we unload everything and ````return 0````, to get back to hbmenu.