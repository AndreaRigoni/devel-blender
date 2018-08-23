# devel-blender
Base setup for bledner development using docker image

This is a autoconf/automake minimal setup to start a new project. It uses Kconfig integration 
provided by https://github.com/AndreaRigoni/autoconf-kconfig as a submodule in conf/kconfig

In the following a easy setup procedure:

<pre>
git clone https://github.com/andrearigoni/devel-blender
cd devel-blender
./bootstrap
../configure --enable-kconfig
# A gui appears to select build options
# Enable Docker Build inside gui

make help 

make
make edit

</pre>

