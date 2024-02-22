---
layout: simple
title: Pico-8
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
PICO-8 is a fantasy console for making, playing, and sharing small
games. PICO-8 is a commercial product by Lexaloffle Games LLP. Versions
are available for Windows, mac OS, Linux, and Raspberry Pi. The
Raspberry Pi version runs on the GameShell, with some set-up.

As of Launcher v1.24, the Launcher now has a built-in PICO-8 installer
to make this even easier! You will copy PICO-8 to your GameShell, then
run this installer to finish set-up.

Follow these instructions to get PICO-8 and install it on your
GameShell. It will run in the splore mode, which lets you browse,
download, and play PICO-8 games.

## Purchase PICO-8

Go here to purchase your copy of PICO-8 if you don’t already own it:
<https://www.lexaloffle.com/pico-8.php#getpico8> (\$15)

Once purchased, visit the downloads page and download the Raspberry Pi
version. This file has a filename similar to: pico-8_0.1.12c_raspi.zip

Tip: Your PICO-8 license includes versions for all platforms. Download
the version for your desktop computer, make PICO-8 games of your own,
and run them on your GameShell!

## Transferring PICO-8 to the GameShell

The Launcher’s PICO-8 installer looks for the zip file in a folder
(directory) with this path: ~/games/PICO-8/ (The ~ means the cpi user’s
“home” directory, containing the games directory where you put various
game ROMs and such. The PICO-8 directory is inside there.)

Connect your GameShell to your wifi network and get its IP address:

Turn on your GameShell. If necessary, connect the GameShell to your
wireless network: Settings, Wi-Fi. In the main launcher menu, select
TinyCloud. This displays the IP address of your GameShell, such as
192.168.0.49. You can transfer files to the GameShell using scp, a file
transfer method based on ssh (Secure Shell). Some file transfer programs
know how to do this, such as Putty SCP for Windows, WinSCP for Windows,
or Transmit for Mac. Connect using the IP address, an account name of
cpi, and a password of cpi.

On Mac and Linux (and also Windows with Putty SCP or the Windows
Subsystem for Linux), you can use a Terminal to do this with a
command-line interface and the scp command. To transfer PICO-8 to the
~/games/PICO-8 directory on the GameShell using the scp command:

scp pico-8_0.1.11g_raspi.zip cpi@192.168.0.49:~/games/PICO-8/ Enter the
password cpi when prompted.

## DevTerm and PICO-8

### CM3 DevTerm (32-bit OS)

The following instructions are copied from a post [lexaloffle
forums](https://www.lexaloffle.com/bbs/?tid=44522).

#### Installation

- You install PICO-8 like you would with any other Raspberry Pi system.
- Open a web browser. (It's the "globe" icon in the Raspian menu bar.)
- If you purchased PICO-8 directly from Lexaloffle, visit
  <https://www.lexaloffle.com/> and sign in with your account. Click
  your username to open the menu, select Downloads. Locate the PICO-8
  Raspberry Pi version, then click "zip" to download. (If you purchased
  PICO-8 from Humble Bundle, Itch.io, or another vendor, follow their
  instructions to download the latest Raspberry Pi version.)
- Open the file explorer (the "folder" icon in the Raspian menu bar),
  then navigate to Downloads to find the file you downloaded.
  Double-click to open the .zip file, then click the Extract files
  button and follow the prompts to select a location for the pico-8
  folder. I keep mine in the pi home folder.

To launch PICO-8, navigate to the pico-8 folder, double-click the pico8
icon, then click Execute. (The process for adding PICO-8 to the
Application menu or the Application Launch Bar is a bit involved, so I
won't go into that here.)

Alternatively, you can start PICO-8 from the command line by executing
the pico8 command:

`   ~/pico-8/pico8`

Note: The rest of these instructions assume some familiarity with the
Linux command line. To get to a command prompt, click the "terminal
window" icon in the Raspian menu bar.

#### PICO-8 full screen and windowed modes

By default, PICO-8 opens to take up the full screen. You can press
Alt+Tab to switch between applications while PICO-8 is running. You can
close PICO-8 by giving it the SHUTDOWN command, or by pressing Alt+Space
to open the window menu then selecting Close.

It is important to remember that PICO-8 hides the mouse cursor when it
is full screen and in console mode or game playing mode. In other modes,
it'll show the cursor, but only if the cursor is positioned in PICO-8's
square display area. This is a special problem for DevTerm because the
mouse could be anywhere on its wide screen, and the trackball moves it
so slowly that it can be frustrating to find it just by moving it
blindly. Instead, press Alt+Space to open the window menu and reveal the
cursor, move the cursor into the PICO-8 area, then press Escape to close
the menu.

To have PICO-8 open in a window instead of full screen, you can use a
command line option when starting PICO-8, like so:

`   ~/pico-8/pico8 -windowed 1`

You can tell PICO-8 to open in a window every time by updating its
configuration file. This file is located at the path
~/.lexaloffle/pico-8/config.txt. (It is not in the pico-8 directory with
the app.) Open this file in a text editor, such as the pico editor (no
relation) that's included with Raspian:

`   pico -w ~/.lexaloffle/pico-8/config.txt`

I recommend the following settings for running PICO-8 windowed on
DevTerm. This puts the window on the right side of the screen and
obscures the borders.

`   window_size 478 478`

`   windowed 1`

`   window_position 808 -26`

To position the window centered on the screen with the window bar
visible, use this window_position:

`   window_position 430 0`

Save the file then exit the editor: in the pico editor, save with Ctrl-O
and press enter when prompted for a filename, then exit with Ctrl-X.
Quit PICO-8 if it is running, then restart it to pick up the new
settings.

When PICO-8 uses the automatic window size (0 0) and position (-1 -1),
Raspian opens a window that's a bit too big for DevTerm. Moreover, the
window borders are obscured, so you can't drag them to resize! To
reposition the PICO-8 window when this happens:

Press Alt+Space to open the window menu, then select Move. Use the
trackball to move the window down so you can see the window bar, then
click the left mouse button to release the window. Drag a corner to
resize the window.

#### Setting up the gamepad buttons

The DevTerm gamepad buttons work with PICO-8, but not out of the box.
You must [configure them](https://pico-8.fandom.com/wiki/Controllers)
with the SDL controllermap utility and PICO-8's controller configuration
file.

Open this article in a browser on your DevTerm, then copy the
configuration line from here:

`    03000000af1e00002400000010010000,ClockworkPI DevTerm,platform:Linux,a:b2,b:b1,x:b3,y:b0,leftx:a0,lefty:a1,`

Select the complete line (from "03000..." to "...lefty:a1," which might
be hidden off the right side of the box as it appears on the BBS) and
copy it to the clipboard (Ctrl+C from a browser). Back at the command
prompt, open the PICO-8 controller configuration file in an editor:

`     pico -w ~/.lexaloffle/pico-8/sdl_controllers.txt`

Move to the bottom of the file then paste the line (Shift+Ctrl+V). Save
and exit. Quit and restart PICO-8, if needed.

The configuration line was generated using the controllermap utility
that comes with SDL. This is not installed by default. If you want to
try this utility yourself, execute these commands in a Terminal window
to download, build, and run the controllermap utility:

`   wget `[`http://libsdl.org/release/SDL2-2.0.7.tar.gz`](http://libsdl.org/release/SDL2-2.0.7.tar.gz)
`       tar -zxvf SDL2-2.0.7.tar.gz`
`       cd SDL2-2.0.7/test`
`       ./configure`
`       make controllermap`
`       ./controllermap 0`

The last command runs the tool and opens a graphical interface. Press
the indicated buttons for the directional pad and action buttons, and
press Space for the rest. The tool prints the configuration line to the
Terminal window then exits. Select the text in the terminal window, then
use Shift+Ctrl+C to copy it to the clipboard. Paste it into the
configuration file, as above.

Try it with Splore! Type SPLORE (or just S) at the PICO-8 command prompt
and play some games with the gamepad buttons.

#### Printing

You can print to the thermal printer from any app that knows how to
print. To download and install the CUPS printer driver, run the
following commands:

`   sudo apt -y install libcups2-dev`
`   git clone `[`https://github.com/clockworkpi/DevTerm.git`](https://github.com/clockworkpi/DevTerm.git)
`   cd DevTerm/devterm_thermal_printer_cups`
`   make`
`   sudo make install`
`   lpoptions -d devterm_printer`

You can test print a simple message like so:

echo "Hi DevTerm!" \| lp

PICO-8 does not have any built-in printing capability. [OR DOES
IT??](https://twitter.com/dan_sanderson/status/1434253649266364417?s=20)

... Not exactly. For this little hack I wrote a [Python
script](https://gist.github.com/dansanderson/3a2a2ff6c6287003d1de77432c4c1109)
that runs in the background and waits for you to EXPORT XXX.LUA.PNG from
PICO-8. When you do this, PICO-8 generates a PNG image of the contents
of the source code editor in the PICO-8 font and colors. The Python
script does some processing of the image to convert it to black text on
a white background, then sends it to the thermal printer.

This hack works even if the contents of the source code editor isn't
actually code, so you could use it to print grocery lists or whatever
from PICO-8. You can experiment with the script to get different
results. I chose elements such as the scaling (180%) mostly for
visibility in the tweet video. This method cuts off the page about
1-1/2" in.

A small warning: during my experiments I had the thermal printer trying
to print large blocks of dark color (black and grey). Not only is it
lousy at this—the paper advance is not very accurate—it tends to trip
the power fault circuitry and shut off the DevTerm. Stick to text and
sparse images, or at least save your work.

`   To list pending print jobs: lpstat -o`
`   To kill a specific print job: cancel `<jobid>
`   To kill all pending print jobs: cancel -a devterm_printer`

### A04/A06 DevTerm (64-bit OS)

From the [lexaloffle forums](https://www.lexaloffle.com/bbs/?pid=71974)
the following commands should get PICO-8 running on a 64-bit ARM
operating system. Refer to this [longer, more detailed post about the
32-bit version](https://www.lexaloffle.com/bbs/?tid=44522) for
additional configuration details that should apply to either.

`   sudo dpkg --add-architecture armhf`
`   sudo apt-get update`
`   sudo apt install libudev1:armhf libsdl2-2.0-0:armhf`
`   sudo reboot now`

After reboot

`   $PATH_TO_PICO/pico8_dyn`

## Welcome to PICO-8!

After it installs, PICO-8 starts in splore mode. From now on, the PICO-8
option in the Launcher will just launch PICO-8 like this.

Move right to find the “Featured” section. If necessary, press B on
\[update\] to load the list. Move up and down to find a game, then press
B to start it.

PICO-8 games use one or both of the A and B buttons. Some games will
refer to these as Z and X, or C and V, because these are the default
keys on a desktop computer. Games may also refer to them as (O) and (X),
which are their “fantasy console” button icons.

To exit a game and return to the Splore game selection menu, press the
GameShell MENU button, then select “Exit to Splore”. (You can also use
the pause menu just to pause your game.)

To exit PICO-8 entirely and return to the GameShell Launcher, exit to
Splore, then press MENU again and select “Shutdown PICO-8”.

Tip: Be careful not to select “Exit to Console” from the shutdown menu.
This puts PICO-8 in its game developer mode. It’s a super fun mode, but
you need a full keyboard to use it or get back out of it. Hold down the
GameShell’s power button to reset if you get stuck here.

Enjoy the games, and come visit the PICO-8 community in the forum to
learn more!

## Resources

- [Original GameShell forum
  post](https://forum.clockworkpi.com/t/how-to-install-pico-8-on-gameshell/1012)
- [Original DevTerm forum
  post](https://www.lexaloffle.com/bbs/?tid=44522)
- [The PICO-8 website](https://www.lexaloffle.com/pico-8.php)
- [The PICO-8 forum](https://www.lexaloffle.com/bbs/?cat=7) (“BBS”,
  where games are published)
- [Lazy Devs video of this installation
  procedure](https://www.youtube.com/watch?v=ltBVKFw88zw), including the
  v1.24 file renaming workaround
- [Lazy Devs video of additional
  steps](https://www.youtube.com/watch?v=4veRSqVHzoI) to enable volume
  buttons and upload PICO-8 cart files directly to the GameShell
- [Dan Sanderson's python printing
  script](https://gist.github.com/dansanderson/3a2a2ff6c6287003d1de77432c4c1109)