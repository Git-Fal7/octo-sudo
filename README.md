## OCTOPI-SUDO

This is a clone of LXQt sudo tool (without LXQt libs). It is the *ONLY* privilege escalation tool supported by Octopi.

It works with doas (default) and sudo.
## Requirements
- qt5-tools
- qmake
- make

## Building
```
git clone https://github.com/git-fal7/octopi-sudo
cd octopi-sudo
mkdir build_dir
cd build_dir/
qmake-qt5 ..
make
```
