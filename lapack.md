## LAPACK

```
$ wget http://www.netlib.org/lapack/lapack-3.5.0.tgz
$ tar xvfz lapack-3.5.0.tgz
$ cd lapack-3.5.0

$ cp make.inc.example make.inc
$ time sudo make 2>&1 | tee m.txt
...
make[1]: ディレクトリ '/home/myid/Downloads/lapack-3.5.0/BLAS/TESTING' に入ります
gfortran  -O2 -frecursive -c sblat1.f -o sblat1.o
gfortran  sblat1.o  \
       ../../librefblas.a  -o ../xblat1s
gfortran: ../../librefblas.a: そのようなファイルやディレクトリはありません
make[1]: *** [../xblat1s] エラー 1
make[1]: ディレクトリ '/home/myid/Downloads/lapack-3.5.0/BLAS/TESTING' から出ます
make: *** [blas_testing] エラー 2

$ cd ../
$ wget http://www.netlib.org/blas/blas.tgz
$ tar xvfz blas.tgz
$ cd BLAS
$ time sudo make 2>&1 | tee m.txt

$ mkdir /home/myid/lapack
$ cp *.a ../home/myid/lapack
$ cd ../lapack-3.5.0
$ cp *.a ../home/myid/lapack

$ cd /home/myid/lapack
$ ls -al

-rw-r--r--. 1 myid myid   735754  4月  1 17:52 2015 blas_LINUX.a
-rw-r--r--. 1 myid myid 10320160  4月  1 17:52 2015 liblapack.a
-rw-r--r--. 1 myid myid   630588  4月  1 17:52 2015 libtmglib.a

$ cd /path/to/openmx/source/
$ vi makefile

LAPACK=/home/myid/lapack

LIB	= -L$(LAPACK) -llapack -ltmglib $(LAPACK)/blas_LINUX.a

```

**<font color=red>l</font>**ib**<font color=red>lapack</font>**.a
<font color=red>-llapack</font>
