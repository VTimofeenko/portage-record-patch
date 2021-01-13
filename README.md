# About
Small utility that automates the steps from [Gentoo Wiki to create quick patches](https://wiki.gentoo.org/wiki/Patches). On the first run it will prompt to create a git repo in the WORKDIR of unpacked package. On subsequent runs it will record the changes to the unpacked package in `/etc/portage/patches/<category>/<package_name>/`

# Example usage:

```
# ebuild $(equery w root-notify-send) clean prepare

# cd /var/tmp/portage/x11-misc/root-notify-send-9999/work
/var/tmp/portage/x11-misc/root-notify-send-9999/work # record-patch "init"
The workdir /var/tmp/portage/x11-misc/root-notify-send-9999/work/root-notify-send-9999 does not seem to be a git repo. You should init it:
cd "/var/tmp/portage/x11-misc/root-notify-send-9999/work/root-notify-send-9999" && git init && git add . && git commit -m 'init'
Should the script init it (y/n)? y
Continuing
Initialized empty Git repository in /var/tmp/portage/x11-misc/root-notify-send-9999/work/root-notify-send-9999/.git/
[master (root-commit) 809aa2c] init
 2 files changed, 9 insertions(+)
 create mode 100644 config.sed
 create mode 100644 root-notify-send
Note: the 'init' comment was discarded

/var/tmp/portage/x11-misc/root-notify-send-9999/work # echo "# Some addition" >> root-notify-send-9999/root-notify-send
/var/tmp/portage/x11-misc/root-notify-send-9999/work # record-patch "some addition"
Recording the changes in /etc/portage/patches/x11-misc/root-notify-send-9999/some-addition.patch
On branch master
nothing to commit, working tree clean
```

