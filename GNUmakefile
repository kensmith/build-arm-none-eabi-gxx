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
:build/sysroot/usr newlib-1.20.0\
;(cd newlib-1.20.0/newlib/libc; tar c include)\
|(cd build/sysroot/usr/;tar xv)\


newlib-1.20.0\
:newlib-1.20.0.tar.gz\
;tar xzvf $<


newlib-1.20.0.tar.gz\
:\
;wget ftp://sources.redhat.com/pub/newlib/newlib-1.20.0.tar.gz


build-binutils\
:build/binutils binutils-2.23\
;cd build/binutils\
;../../binutils-2.23/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


binutils-2.23\
:binutils-2.23.tar.gz\
;tar xzvf $<


binutils-2.23.tar.gz\
:\
;wget ftp://ftp.gnu.org/pub/gnu/binutils/binutils-2.23.tar.gz


build-newlib\
:build/newlib newlib-1.20.0\
;cd build/newlib\
;../../newlib-1.20.0/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


build-gcc-bootstrap\
:build/gcc-bootstrap gcc-4.7.2\
;cd build/gcc-bootstrap\
;../../gcc-4.7.2/configure\
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


gcc-4.7.2\
:gcc-4.7.2.tar.bz2\
;tar xjvf $<


gcc-4.7.2.tar.bz2\
:\
;wget ftp://ftp.gnu.org/pub/gnu/gcc/gcc-4.7.2/gcc-4.7.2.tar.bz2


build-gcc-final\
:build/gcc-final gcc-4.7.2\
;cd build/gcc-final\
;../../gcc-4.7.2/configure\
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
:build/gdb gdb-7.5\
;cd build/gdb\
;../../gdb-7.5/configure\
 --target=arm-none-eabi\
 --enable-interwork\
 --enable-multilib\
&& make\
&& sudo make install


gdb-7.5\
:gdb-7.5.tar.bz2\
;tar xjvf $<


gdb-7.5.tar.bz2\
:\
;wget ftp://ftp.gnu.org/pub/gnu/gdb/gdb-7.5.tar.bz2


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
 binutils-2.23\
 gcc-4.7.2\
 gdb-7.5\
 newlib-1.20.0
