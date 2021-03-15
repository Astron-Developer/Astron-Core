
Debian
====================
This directory contains files used to package astrond/astron-qt
for Debian-based Linux systems. If you compile astrond/astron-qt yourself, there are some useful files here.

## astron: URI support ##


astron-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install astron-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your astron-qt binary to `/usr/bin`
and the `../../share/pixmaps/astron128.png` to `/usr/share/pixmaps`

astron-qt.protocol (KDE)

