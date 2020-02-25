# HElib Quickstart

Minimum instructions for installing [HElib](https://github.com/homenc/HElib) and compiling the examples.  
Adapted from [HElib/INSTALL.md](https://github.com/homenc/HElib/blob/master/INSTALL.md)

### Dependencies

```bash
apt update
apt install cmake make m4 patchelf g++ git
```

### Installation

```bash
git clone https://github.com/homenc/HElib.git
cd HElib/

mkdir build
cd build/

cmake -DPACKAGE_BUILD=ON ..
make -j8 # Adjust the desired number of jobs

# At the time of writing, `make install` was broken
# (copying to PREFIX/helib_pack instead of PREFIX).
sudo cp -r helib_pack/* /usr/local/
sudo ldconfig
```

### Examples

```bash
# In HElib/
cd examples/binaryArith_example/
g++ -std=c++14 -I/usr/local/include/helib -L/usr/local/lib64 binaryArith_example.cpp \
  -lhelib -lntl -lpthread -o binaryArith_example
./binaryArith_example
```
