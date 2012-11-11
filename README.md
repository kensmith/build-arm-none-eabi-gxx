You'll need mpfr, mpc, gmp, isl, cloog, a proper build
environment and anything else you don't have that's listed
here.

http://gcc.gnu.org/install/prerequisites.html

You should be able to run `make` and when it's all done
you'll have a working arm-none-eabi-g++ toolchain with all
the fixin's. This build script uses sudo to install things
so you'll either have to type your password in from time to
time or you'll have to have NOPASSWD in your /etc/sudoers
for your login group.

Tested on Arch Linux circa end of 2012. Support for building
in parallel left as an exercise. (IOW, don't do `make -j`.)

vim:tw=60:
