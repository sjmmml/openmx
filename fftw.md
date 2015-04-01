## FFTW

OpenMPIインストールする前にFFTWインストールする。 
[Download](http://www.fftw.org/download.html)

```
$ wget http://www.fftw.org/fftw-3.3.4.tar.gz

$ time sudo ../fftw-3.3.4/configure --enable-threads --enable-openmp --enable-mpi --enable-sse2 -prefix=/home/myid/fftw LDFLAGS=-L/home/myid/openmpi/lib CPPFLAGS=-I/home/myid/openmpi/include 2>&1 | tee c.txt
....
config.status: executing libtool commands

real	0m15.768s
user	0m5.569s
sys		0m4.533s
```

install in `/home/myid/fftw/`

```
-prefix=/home/myid/fftw
```


```
$ time sudo make 2>&1 | tee m.txt
...
make[1]: ディレクトリ '/home/myid/Downloads/fftw_build' から出ます

real	1m23.638s
user	1m6.508s
sys		0m13.032s

$ time sudo make install 2>&1 | tee mi.txt
...
make[1]: ディレクトリ '/home/myid/Downloads/fftw_build/m4' から出ます

real	0m19.225s
user	0m1.412s
sys	0m0.357s
```

```
$ cd /home/myid/fftw/lib
$ ls -al
-rw-r--r--. 1 root root 3191804  4月  1 16:59 2015 libfftw3.a
-rwxr-xr-x. 1 root root     904  4月  1 16:59 2015 libfftw3.la
-rw-r--r--. 1 root root  187456  4月  1 16:59 2015 libfftw3_mpi.a
-rwxr-xr-x. 1 root root    1087  4月  1 16:59 2015 libfftw3_mpi.la
-rw-r--r--. 1 root root   41798  4月  1 16:59 2015 libfftw3_omp.a
-rwxr-xr-x. 1 root root     958  4月  1 16:59 2015 libfftw3_omp.la
-rw-r--r--. 1 root root   45594  4月  1 16:59 2015 libfftw3_threads.a
-rwxr-xr-x. 1 root root     970  4月  1 16:59 2015 libfftw3_threads.la
drwxr-xr-x. 2 root root    4096  4月  1 16:59 2015 pkgconfig
```

```
$ cd /path/to/openmx/source
$ vi makefiile

FFTW=/home/myid/fftw

LIB	= -L$(FFTW)/lib -lfftw3 -lfftw3_mpi -lfftw3_omp -lfftw3_threads
```
