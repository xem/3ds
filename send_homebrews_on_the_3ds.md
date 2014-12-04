# Send homebrews on the 3DS

Two files are needed for a 3DS homebrew to be run with Ninjhax: a .3dsx file and a .smdh file.

If you want to run homebrews on your console, you can use your computer to place them in the "3ds" folder of your SD / microSD card.

Feel free organize your homebrews into subfolders.

You can also upload them directly using wi-fi, if your PC and 3DS are connected to the same local network:

1. Start hbmenu.
2. Start the ftPONY homebrew (or [ftBRONY](https://github.com/mtheall/ftbrony))
3. Note the IP and port displayed on the upper screen (for example: "IP: 192.168.0.128 port 5000")
4. Start a FTP client on your desktop, and use these credentials to get connected.
5. If asked, choose "anonymous connection".
6. You should now see your SD / microSD card's filesystem and be able to drag & drop files and folders in the "3ds" folder of your card.
7. Press B to quit ftPONY and launch your new apps.

<img src="http://img.ctrlv.in/img/14/11/22/54709afe2f047.png" width=700>

If you're a Linux user (or a Windows / Mac user using cat or netcat) and want to perform quick tests during the development of of your homebrews:

1. Download the latest version of [hbmenu](https://github.com/smealum/3ds_hb_menu), build it and install it on your SD card.
2. Start hbmenu
3. Press the Y button
4. On your PC open a terminal (or command promt when using Windows)
5. Browse to the directory your .3dsx file is located in.
6. use the command: ````cat name.3dsx | nc ip 9000```` Where you replace "name.3dsx" with your .3dsx file and ip with the IP displayed on the bottom screen.
7. After a little moment (depending on the size of your .3dsx file) it will automatically boot your homebrew.

Note: This is only useful for testing as the file won't stay on the 3DS after it is closed.