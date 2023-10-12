# Configuring tmux in a rootless jailbreak on iOS 15

## Prerequisites
Before proceeding with tmux configuration, make sure you have installed the following components:

- [OpenSSH](sileo://package/openssh) and [tmux](sileo://package/tmux) from the Procursus Team.
- [NewTerm 3 Beta](sileo://package/ws.hbang.newterm3) from HASHBANG.

## Fixing the "tmux: need UTF-8 locale (LC_CTYPE) but have ANSII" error
If you encounter the "tmux: need UTF-8 locale (LC_CTYPE) but have ANSII" error, follow these steps:

1. In `var/jb/usr/share/locale/UTF-8`, replace the existing LC_CTYPE file with the one from this repository, as the one from Procursus is empty.
2. In `var/jb/usr/etc`, add the following lines to the "profile" file:

`export LC_CTYPE=UTF-8`


## Fixing the "error connecting to /private/preboot/.../jb-GoDElU/procursus/tmp/tmux-0/default (File name too long)" error
If you're facing the "error connecting to /private/preboot/.../jb-GoDElU/procursus/tmp/tmux-0/default (File name too long)" error, follow these steps:

1. Create a "tmp" folder in `var/mobile/Documents`.
2. In `var/jb/usr/etc`, add the following lines to the "profile" file:

`export TMUX_TMPDIR=/var/mobile/Documents/tmp`

With these steps completed, tmux should work as expected.





