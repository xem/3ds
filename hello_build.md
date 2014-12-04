# Hello build!

We will now see how to build our project.

"Building" means generating the files that will be played on your console.

- Open a CLI (command line interface). If you're on Windows, press Shift + right click on the template folder and choose "Open a command line interface here".
- type ````make```` and press enter.
- After a few seconds, the process finishes. (you can ignore the warning messages).
- A "build" folder, and three files (.elf, .3dsx and .smdh) appeared in the template folder.
- Send the .3dsx and the .smdh files on your SD card to test the homebrew on real hardware.

When you will work on 3DS projects, you can of course rebuild them at any time to test your changes, from the CLI again:

- run the ````make clean```` command. (this will erase the build files)
- run the ````make```` command again.

(generally, the clean isn't even necessary, you can decide to do it only if the build fails)

Similarly, you can download the sources of an open-source homebrew and build it using ````make````.

Windows users: if you get compilation errors during the build, check your environment variables:

- Right-click "This PC" and select "Properties".
- Click "Advanced system settings" (on the left).
- Click "Environment Variables..." (on the bottom).
- Highlight the "PATH" variable (on top), click "Edit...".
- Check that your DevkitARM and Python install folders are present (ex: "C:\DevkitPro\DevkitARM\bin", "C:\Python34").
- If one (or both) are not present, add them at the end, saparated by ";". Save and quit.