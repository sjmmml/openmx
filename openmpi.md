## Open MPI

[OpenMPI](http://www.open-mpi.org/software/ompi/)

```
$ wget http://www.open-mpi.org/software/ompi/v1.8/downloads/openmpi-1.8.4.tar.gz
$ tar vxfz openmpi-1.8.4.tar.gz

$ mkdir openmpi_build
$ mkdir /home/myid/openmpi
$ cd openmpi_build
$ time sudo ../openmpi-1.8.4/configure --prefix="/home/myid/openmpi" 2>&1 | tee c.txt

...
config.status: executing libtool commands

real	2m11.131s
user	1m8.109s
sys		0m46.936s

$ time sudo make 2>&1 | tee m.txt

real	9m41.927s
user	7m48.092s
sys		1m27.072s

$ time sudo make install 2>&1 | tee mi.txt

real	0m54.039s
user	0m38.895s
sys		0m7.640s
```

```
$ vi ~/.bashrc

export PATH=/home/myid/openmpi/bin:$PATH

$ source ~/.bashrc
```
