SX
==

sx is a simple alternative to both xinit and startx for starting an Xorg server
[0].

Configuration
-------------

Ensure that you have sx installed first:

    $ kiss b sx
    $ kiss i sx

The default XDG_DATA_HOME and XDG_CONFIG_HOME directories can be modified via
environment variables:

    $ echo "export XDG_DATA_HOME=$HOME/.config" >> ~/.profile
    $ echo "export XDG_CONFIG_HOME=$HOME/.config" >> ~/.profile

Create the required directories and rc file:

    $ mkdir -p ~/.config/sx
    $ touch ~/.config/sx/sxrc
    $ chmod +x ~/.config/sx/sxrc

At this point, you can add content to your sxrc file. For example, if you wanted
to start sowm window manager, you could add the following:

    $ echo "exec sowm" >> ~/.config/sx/sxrc

You should now be able to start your window manager and X server with sx:

    $ sx

Start after login
-----------------

Add the following to the bottom of your ~/.profile file:

    $ [ -z "$DISPLAY" ] && [ "$(tty)" = /dev/tty1 ] && exec sx

If you would like to remain logged in when the X session ends, remove exec.

References
----------

[0]: https://github.com/Earnestly/sx

