---
layout: simple
title: How-Tos_and_Tweaks
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
## Window Manipulation

With Xfce on the Devterm A04 and A06, it can be difficult to manipulate
windows that are taller than the screen. There are two lesser-known
modifiers that can aid here:

- **Alt + Left Drag**: Move the window from any position
- **Alt + Right Drag**: Resize the window from any position

These two modifier combinations can move a window from any position,
regardless of how far the title bar is above the top of the screen (or
the resize handle is below the bottom).

## Screen Adjustments with Xrandr

If the screen size is still too small for your use with the Alt
modifiers above, you can use Xrandr to enable panning or scaling on the
display. To enable panning:

    xrandr --fb 1280x960 --output DSI-1 --panning 960x0

Or to enable scaling:

    xrandr --output DSI-1 --scale 2x2

Fractional values are valid too (like `--scale 1.5x1.5`)

## SDL2 Joystick Profile

Some games rely on SDL2 gamepad detection, which won't detect the
DevTerm pad and buttons by default. To get the gamepad detected, add the
following line to the `.profile` file in your home folder:

    export SDL_GAMECONTROLLERCONFIG="03000000af1e00002400000010010000,ClockworkPI DevTerm,platform:Linux,a:b2,b:b1,x:b3,y:b0,back:b8,start:b9,leftx:a0,lefty:a1,"

And log out/log back in.