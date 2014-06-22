Нужно войти для начало cd /home и сюда исходники.
если меркуриал(hg) то для скачивания на тачку hg clone https://..........
cd название_скачаной_папки_с_исходами
cd /home/asgar & git pull ссылка на bitbucker компиляция.
mkdir build
cd build
cmake ../ -DPREFIX=/home/server -DCMAKE_C_FLAGS="-march=corei7 -m64 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O3 -pipe -pipe -msse3 -fomit-frame-pointer -ffast-math -fno-strength-reduce -fno-strict-aliasing -frename-registers -ggdb -g3" -DCMAKE_CXX_FLAGS="${CMAKE_C_FLAGS}" -DCMAKE_BUILD_TYPE="RelWithDebInfo"
дальше make -j 9 и make install

или 
cd /opt
rm -r asgarcore
hg clone https://bitbucket.org/blaskred/asgarcore/
cd asgarcore
mkdir build && cd build
patch -p1 < ../../diff.patch
cmake ../ -DPREFIX=/home/server/xzwow -DWITHOUT_GIT=true -DCMAKE_BUILD_TYPE="Debug"
make -j 8 && make install -j 8

Потом базы WORLD 
mysql -uroot -ppass_word_root -Dworld_test --default-character-set=utf8 < /home/world.sql

