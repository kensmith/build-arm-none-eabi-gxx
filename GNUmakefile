gcc-version := 4.8.2
newlib-version := 2.0.0
gdb-version := 7.6.1
binutils-version := 2.23

.PHONY:\
 all\
 build-binutils\
 build-newlib\
 build-gcc-bootstrap\
 build-gcc-final\
 build-gdb\
 clean


all\
:build-sysroot\
 build-binutils\
 build-gcc-bootstrap\
 build-newlib\
 build-gcc-final\
 build-gdb


build-sysroot\
:build/sysroot/usr newlib-$(newlib-version)\
;(cd newlib-$(newlib-version)/newlib/libc; tar c include)\
|(cd build/sysroot/usr/;tar xv)\


newlib-$(newlib-version)\
:newlib-$(newlib-version).tar.gz\
;tar xzvf $<


newlib-$(newlib-version).tar.gz\
:\
;wget ftp://sources.redhat.com/pub/newlib/newlib-$(newlib-version).tar.gz


build-binutils\
:build/binutils binutils-$(binutils-version)\
;cd build/binutils\
;../../binutils-$(binutils-version)/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


binutils-$(binutils-version)\
:binutils-$(binutils-version).tar.gz\
;tar xzvf $<


binutils-$(binutils-version).tar.gz\
:\
;wget ftp://ftp.gnu.org/pub/gnu/binutils/binutils-$(binutils-version).tar.gz


build-newlib\
:build/newlib newlib-$(newlib-version)\
;cd build/newlib\
;../../newlib-$(newlib-version)/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


build-gcc-bootstrap\
:build/gcc-bootstrap gcc-$(gcc-version)\
;cd build/gcc-bootstrap\
;../../gcc-$(gcc-version)/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
 --enable-languages=c\
 --with-newlib\
 --with-build-sysroot=sysroot\
 --disable-threads\
 --disable-libmudflap\
 --disable-libssp\
 --disable-libgomp\
 --disable-libquadmath\
 --disable-shared\
 --disable-zlib\
 --disable-nls\
&& make\
&& sudo make install


gcc-$(gcc-version)\
:gcc-$(gcc-version).tar.bz2\
;tar xjvf $<


gcc-$(gcc-version).tar.bz2\
:\
;wget ftp://ftp.gnu.org/pub/gnu/gcc/gcc-$(gcc-version)/gcc-$(gcc-version).tar.bz2


build-gcc-final\
:build/gcc-final gcc-$(gcc-version)\
;cd build/gcc-final\
;../../gcc-$(gcc-version)/configure\
 --target=arm-none-eabi\
 --with-newlib\
 --disable-threads\
 --disable-libmudflap\
 --disable-libssp\
 --disable-libgomp\
 --disable-libquadmath\
 --disable-shared\
 --disable-zlib\
 --disable-nls\
 --enable-multilib\
 --enable-interwork\
 --enable-languages=c,c++\
&& make\
&& sudo make install


build-gdb\
:build/gdb gdb-$(gdb-version)\
;cd build/gdb\
;../../gdb-$(gdb-version)/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


gdb-$(gdb-version)\
:gdb-$(gdb-version).tar.bz2\
;tar xjvf $<


gdb-$(gdb-version).tar.bz2\
:\
;wget ftp://ftp.gnu.org/pub/gnu/gdb/gdb-$(gdb-version).tar.bz2


build/sysroot/usr\
 build/newlib\
 build/gcc-bootstrap\
 build/gcc-final\
 build/binutils\
 build/gdb\
:\
;mkdir -p $@


clean\
:\
;rm -Rf\
 build\
 binutils-$(binutils-version)\
 gcc-$(gcc-version)\
 gdb-$(gdb-version)\
 newlib-$(newlib-version)
