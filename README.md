# Configuring tmux in a rootless jailbreak on iOS 15

I will explain how I resolved the two issues that I was facing. If you haven't encountered these problems, there's no need to apply the respective fixes.

## Prerequisites
Before proceeding with tmux configuration, make sure you have installed the following components:

- [OpenSSH](sileo://package/openssh) and [tmux](sileo://package/tmux) from the Procursus Team.
- [NewTerm 3 Beta](sileo://package/ws.hbang.newterm3) from HASHBANG.

## Fixing the "tmux: need UTF-8 locale (LC_CTYPE) but have ANSII" error
If you encounter the "tmux: need UTF-8 locale (LC_CTYPE) but have ANSII" error, follow these steps:

1. In `var/jb/usr/share/locale/UTF-8`, replace the existing LC_CTYPE file with the [one from this repository](https://github.com/pedromopi/tmux/blob/main/LC_CTYPE), as the one from Procursus is empty.
2. In `var/jb/usr/etc/profile.d`, create (or edit) "personal.sh" and add the following line to the file:

`export LC_CTYPE=UTF-8`


## Fixing the "error connecting to /private/preboot/.../jb-GoDElU/procursus/tmp/tmux-0/default (File name too long)" error
If you're facing the "error connecting to /private/preboot/.../jb-GoDElU/procursus/tmp/tmux-0/default (File name too long)" error, follow these steps:

1. Create a "tmp" folder in `var/mobile/Documents`.
2. In `var/jb/usr/etc/profile.d`, create (or edit) "personal.sh" and add the following line to the file:

`export TMUX_TMPDIR=/var/mobile/Documents/tmp`

## Running tmux

With these steps completed, tmux should work as expected and you can run in NewTerm:

`tmux -u new-session -s MySessionName`

## Still Encountering Problems?

If, after logging in with 'su' and your password, you are still facing issues, you can check if the previously defined variables are available by running the "env" command in NewTerm. You should see the variables listed. If they do not appear, you can set them manually by using the following commands:

````
export LC_CTYPE=UTF-8
export TMUX_TMPDIR=/var/mobile/Documents/tmp
tmux -u new-session -s py
````





