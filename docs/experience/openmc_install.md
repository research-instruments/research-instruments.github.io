**Инструкция по установке openmc**

Сначала следует установить wsl

Для этого нужно открыть командную строку windows от имени администратора и ввести команду wsl --install, а потом следовать инструкциям

**Далее нужно открыть wsl командой bash на диске (например c:) и последовательно ввести следующие команды:**

sudo apt-get install gfortran

sudo apt install g++

sudo apt-get install cmake

sudo apt-get update

sudo apt install python3-pip

sudo apt-get install libhdf5-dev

sudo apt-get install git

sudo apt-get install cython

sudo apt-get install python-numpy

python3 -m pip install -U pip

python3 -m pip install -U matplotlib

sudo apt-get install python3-matplotlib

sudo apt-get install python3-scipy

sudo apt-get install python3-numexpr

sudo apt-get install python-imaging-tk

sudo apt install imagemagick

sudo add-apt-repository ppa:webupd8team/java

git clone https://github.com/mit-crpg/openmc.git

cd openmc

git checkout master

mkdir build&& cd build

cmake ..

make

sudo make install

cd ..

git pull

pip install .

**Дашанова Е.А.**
