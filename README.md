armvo@LAPTOP-V7PSSN9N:~$ export GITHUB_USERNAME=AtabekIsm
armvo@LAPTOP-V7PSSN9N:~$ cd ${GITHUB_USERNAME}/workspace
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ pushd .
~/AtabekIsm/workspace ~/AtabekIsm/workspace
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ source /scripts/activate
-bash: /scripts/activate: No such file or directory
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ source scripts/activate
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab02.git projects/lab03
fatal: destination path 'projects/lab03' already exists and is not an empty directory.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git remote remove origin
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ -std=c++11 -I./../../include -c ../../sources/print.cpp
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls print.o
print.o
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ nm print.o | grep print
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ar rvs print.a print.o
ar: creating print.a
a - print.o
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ file print.a
print.a: current ar archive
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ -std=c++11 -I./../../include -c ../../examples/example1.
cpp
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls example1.o
example1.o
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ example1.o print.a -o example1
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ./example1 && echo
hello
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example2.cpp
cc1plus: fatal error: examples/example2.cpp: No such file or directory
compilation terminated.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ -std=c++11 -I./../../include -c ../../examples/example2.
cpp
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ nm example2.o
0000000000000000 V DW.ref.__gxx_personality_v0
                 U _Unwind_Resume
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED2Ev
0000000000000000 n _ZNSt15__new_allocatorIcED5Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZSt21ios_base_library_initv
0000000000000000 r _ZStL19piecewise_construct
                 U __gxx_personality_v0
                 U __stack_chk_fail
0000000000000000 T main
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ g++ example2.o print.a -o example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ./example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat log.txt && echo
hello
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf example1.o example2.o print.o
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf print.a
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf example1 example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf log.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(print)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build
Command 'cmake' not found, but can be installed with:
sudo snap install cmake  # version 4.0.1, or
sudo apt  install cmake  # version 3.27.8-1build1
See 'snap info cmake' for additional versions.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ sudo apt install cmake
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  alsa-topology-conf alsa-ucm-conf aspell aspell-en bubblewrap dictionaries-common docbook-xml emacsen-common
  enchant-2 glib-networking glib-networking-common glib-networking-services gstreamer1.0-gl gstreamer1.0-plugins-base
  gstreamer1.0-x hunspell-en-us libaa1 libasound2-data libasound2t64 libaspell15 libasyncns0 libavc1394-0 libcaca0
  libcdparanoia0 libdv4t64 libenchant-2-2 libevdev2 libfile-basedir-perl libflac12t64 libfontenc1 libgles2
  libgraphene-1.0-0 libgstreamer-gl1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libhandy-1-0
  libharfbuzz-icu0 libhunspell-1.7-0 libhyphen0 libiec61883-0 libinput-bin libinput10 libio-stringy-perl
  libipc-system-simple-perl libjson-glib-1.0-0 libjson-glib-1.0-common libmanette-0.2-0 libmp3lame0 libmpg123-0t64
  libmtdev1t64 libnautilus-extension4 libncurses6 libogg0 libopus0 liborc-0.4-0t64 libproxy1v5 libpulse0 libraw1394-11
  libshout3 libsndfile1 libspeex1 libtag1v5 libtag1v5-vanilla libtheora0 libtwolame0 libv4l-0t64 libv4lconvert0t64
  libvisual-0.4-0 libvorbis0a libvorbisenc2 libvpx9 libvte-2.91-0 libvte-2.91-common libwacom-common libwacom9
  libwavpack1 libwebpdemux2 libwebpmux3 libwebrtc-audio-processing1 libwoff1 libxatracker2 libxcb-shape0 libxcb-util1
  libxcvt0 libxfont2 libxft2 libxkbfile1 libxslt1.1 libxss1 libxv1 libxvmc1 libxxf86dga1 sgml-data x11-xkb-utils xcvt
  xdg-dbus-proxy xfonts-base xfonts-encodings xfonts-utils yelp-xsl
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  cmake-data libarchive13t64 libjsoncpp25 librhash0 libuv1t64 make
Suggested packages:
  cmake-doc cmake-format elpa-cmake-mode ninja-build lrzip make-doc
The following NEW packages will be installed:
  cmake cmake-data libarchive13t64 libjsoncpp25 librhash0 libuv1t64 make
0 upgraded, 7 newly installed, 0 to remove and 105 not upgraded.
Need to get 14.2 MB of archives.
After this operation, 50.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libuv1t64 amd64 1.48.0-1.1build1 [97.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libarchive13t64 amd64 3.7.2-2ubuntu0.4 [382 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libjsoncpp25 amd64 1.9.5-6build1 [82.8 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 librhash0 amd64 1.4.3-3build1 [129 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble/main amd64 cmake-data all 3.28.3-1build7 [2155 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble/main amd64 cmake amd64 3.28.3-1build7 [11.2 MB]
Get:7 http://archive.ubuntu.com/ubuntu noble/main amd64 make amd64 4.3-4.1build2 [180 kB]
Fetched 14.2 MB in 4s (3473 kB/s)
Selecting previously unselected package libuv1t64:amd64.
(Reading database ... 50709 files and directories currently installed.)
Preparing to unpack .../0-libuv1t64_1.48.0-1.1build1_amd64.deb ...
Unpacking libuv1t64:amd64 (1.48.0-1.1build1) ...
Selecting previously unselected package libarchive13t64:amd64.
Preparing to unpack .../1-libarchive13t64_3.7.2-2ubuntu0.4_amd64.deb ...
Unpacking libarchive13t64:amd64 (3.7.2-2ubuntu0.4) ...
Selecting previously unselected package libjsoncpp25:amd64.
Preparing to unpack .../2-libjsoncpp25_1.9.5-6build1_amd64.deb ...
Unpacking libjsoncpp25:amd64 (1.9.5-6build1) ...
Selecting previously unselected package librhash0:amd64.
Preparing to unpack .../3-librhash0_1.4.3-3build1_amd64.deb ...
Unpacking librhash0:amd64 (1.4.3-3build1) ...
Selecting previously unselected package cmake-data.
Preparing to unpack .../4-cmake-data_3.28.3-1build7_all.deb ...
Unpacking cmake-data (3.28.3-1build7) ...
Selecting previously unselected package cmake.
Preparing to unpack .../5-cmake_3.28.3-1build7_amd64.deb ...
Unpacking cmake (3.28.3-1build7) ...
Selecting previously unselected package make.
Preparing to unpack .../6-make_4.3-4.1build2_amd64.deb ...
Unpacking make (4.3-4.1build2) ...
Setting up libuv1t64:amd64 (1.48.0-1.1build1) ...
Setting up make (4.3-4.1build2) ...
Setting up libjsoncpp25:amd64 (1.9.5-6build1) ...
Setting up librhash0:amd64 (1.4.3-3build1) ...
Setting up cmake-data (3.28.3-1build7) ...
Setting up libarchive13t64:amd64 (3.7.2-2ubuntu0.4) ...
Setting up cmake (3.28.3-1build7) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (1.9s)
CMake Error at CMakeLists.txt:5 (add_library):
  Cannot find source file:

    /home/armvo/AtabekIsm/workspace/projects/lab03/sources/print.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:5 (add_library):
  No SOURCES given to target: print


CMake Generate step failed.  Build files cannot be regenerated correctly.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd sources/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/sources$ cmake -H. -B_build
CMake Error: The source directory "/home/armvo/AtabekIsm/workspace/sources" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/sources$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls
CMakeLists.txt  LICENSE  README.md  _build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd sources/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/sources$ ls
print.cpp
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/sources$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ ls
LICENSE  README.md  examples  include  node  projects  reports  scripts  sources  tasks
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls
CMakeLists.txt  LICENSE  README.md  _build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(print)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
CMake Error at CMakeLists.txt:5 (add_library):
  Cannot find source file:

    /home/armvo/AtabekIsm/workspace/projects/lab03/sources/print.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:5 (add_library):
  No SOURCES given to target: print


CMake Generate step failed.  Build files cannot be regenerated correctly.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cd /
armvo@LAPTOP-V7PSSN9N:/$ ls
bin                boot  etc   init  lib.usr-is-merged  lost+found  mnt  proc  run   sbin.usr-is-merged  srv  tmp  var
bin.usr-is-merged  dev   home  lib   lib64              media       opt  root  sbin  snap                sys  usr
armvo@LAPTOP-V7PSSN9N:/$ cd home/
armvo@LAPTOP-V7PSSN9N:/home$ ls
armvo
armvo@LAPTOP-V7PSSN9N:/home$ cd armvo/
armvo@LAPTOP-V7PSSN9N:~$ ls
AtabekIsm  snap
armvo@LAPTOP-V7PSSN9N:~$ cd AtabekIsm/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm$ ls
workspace
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm$ cd workspace/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ ls
LICENSE  README.md  examples  include  node  projects  reports  scripts  sources  tasks
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls
CMakeLists.txt  LICENSE  README.md  _build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ edit CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/armvo/AtabekIsm/workspace/projects/lab03/_build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/home/armvo/AtabekIsm/workspace/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}../../examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}../../examples/example2.cpp)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
CMake Error at CMakeLists.txt:8 (add_executable):
  Cannot find source file:

    /home/armvo/AtabekIsm/workspace/projects/examples/example1.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:9 (add_executable):
  Cannot find source file:

    /home/armvo/AtabekIsm/workspace/projects/examples/example2.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:8 (add_executable):
  No SOURCES given to target: example1


CMake Error at CMakeLists.txt:9 (add_executable):
  No SOURCES given to target: example2


CMake Generate step failed.  Build files cannot be regenerated correctly.
gmake: *** [Makefile:179: cmake_check_build_system] Error 1
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ ls
LICENSE  README.md  examples  include  node  projects  reports  scripts  sources  tasks
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls
CMakeLists.txt  LICENSE  README.md  _build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ ls
lab02  lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects$ cd ..
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ ls
LICENSE  README.md  examples  include  node  projects  reports  scripts  sources  tasks
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd projects/lab03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls
CMakeLists.txt  LICENSE  README.md  _build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ edit CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ edit CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/armvo/AtabekIsm/workspace/projects/lab03/_build
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/home/armvo/AtabekIsm/workspace/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/home/armvo/AtabekIsm/workspace/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build --target print
[100%] Built target print
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build --target example1
[ 50%] Built target print
[100%] Built target example1
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build --target example2
[ 50%] Built target print
[100%] Built target example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ ls -la _build/libprint.a
-rw-r--r-- 1 armvo armvo 2246 May  5 22:23 _build/libprint.a
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ _build/example1 && echo
hello
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ _build/example2
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat log.txt && echo
hello
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf log.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git clone https://github.com/tp-labs/lab03 tmp
Cloning into 'tmp'...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61 (from 1)
Receiving objects: 100% (91/91), 1.02 MiB | 49.00 KiB/s, done.
Resolving deltas: 100% (41/41), done.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ mv -f tmp/CMakeLists.txt .
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ rm -rf tmp
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cat CMakeLists.txt
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
CMake Error at CMakeLists.txt:10 (add_library):
  Cannot find source file:

    /home/armvo/AtabekIsm/workspace/projects/lab03/sources/print.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm
  .ccm .cxxm .c++m .h .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90
  .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:10 (add_library):
  No SOURCES given to target: print


CMake Generate step failed.  Build files cannot be regenerated correctly.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ edit CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/armvo/AtabekIsm/workspace/projects/lab03/_build
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ cmake --build _build --target install
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/armvo/AtabekIsm/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/armvo/AtabekIsm/workspace/projects/lab03/_install/include
-- Installing: /home/armvo/AtabekIsm/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/armvo/AtabekIsm/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/armvo/AtabekIsm/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ tree _install
Command 'tree' not found, but can be installed with:
sudo snap install tree  # version 2.1.3+pkg-5852, or
sudo apt  install tree  # version 2.1.1-2
See 'snap info tree' for additional versions.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ sudo apt install tree
[sudo] password for armvo:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  alsa-topology-conf alsa-ucm-conf aspell aspell-en bubblewrap dictionaries-common docbook-xml emacsen-common
  enchant-2 glib-networking glib-networking-common glib-networking-services gstreamer1.0-gl gstreamer1.0-plugins-base
  gstreamer1.0-x hunspell-en-us libaa1 libasound2-data libasound2t64 libaspell15 libasyncns0 libavc1394-0 libcaca0
  libcdparanoia0 libdv4t64 libenchant-2-2 libevdev2 libfile-basedir-perl libflac12t64 libfontenc1 libgles2
  libgraphene-1.0-0 libgstreamer-gl1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libhandy-1-0
  libharfbuzz-icu0 libhunspell-1.7-0 libhyphen0 libiec61883-0 libinput-bin libinput10 libio-stringy-perl
  libipc-system-simple-perl libjson-glib-1.0-0 libjson-glib-1.0-common libmanette-0.2-0 libmp3lame0 libmpg123-0t64
  libmtdev1t64 libnautilus-extension4 libncurses6 libogg0 libopus0 liborc-0.4-0t64 libproxy1v5 libpulse0 libraw1394-11
  libshout3 libsndfile1 libspeex1 libtag1v5 libtag1v5-vanilla libtheora0 libtwolame0 libv4l-0t64 libv4lconvert0t64
  libvisual-0.4-0 libvorbis0a libvorbisenc2 libvpx9 libvte-2.91-0 libvte-2.91-common libwacom-common libwacom9
  libwavpack1 libwebpdemux2 libwebpmux3 libwebrtc-audio-processing1 libwoff1 libxatracker2 libxcb-shape0 libxcb-util1
  libxcvt0 libxfont2 libxft2 libxkbfile1 libxslt1.1 libxss1 libxv1 libxvmc1 libxxf86dga1 sgml-data x11-xkb-utils xcvt
  xdg-dbus-proxy xfonts-base xfonts-encodings xfonts-utils yelp-xsl
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  tree
0 upgraded, 1 newly installed, 0 to remove and 105 not upgraded.
Need to get 47.1 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/universe amd64 tree amd64 2.1.1-2ubuntu3 [47.1 kB]
Fetched 47.1 kB in 1s (57.1 kB/s)
Selecting previously unselected package tree.
(Reading database ... 54149 files and directories currently installed.)
Preparing to unpack .../tree_2.1.1-2ubuntu3_amd64.deb ...
Unpacking tree (2.1.1-2ubuntu3) ...
Setting up tree (2.1.1-2ubuntu3) ...
Processing triggers for man-db (2.12.0-4build2) ...
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ tree _install
_install
├── cmake
│   ├── print-config-noconfig.cmake
│   └── print-config.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

4 directories, 4 files
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git add CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git commit -m"added CMakeLists.txt"
[main 466688e] added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push origin master
error: src refspec master does not match any
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push origin main
Username for 'https://github.com': AtabekIsm
Password for 'https://AtabekIsm@github.com':
Enumerating objects: 18, done.
Counting objects: 100% (18/18), done.
Delta compression using up to 12 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (18/18), 9.34 KiB | 9.34 MiB/s, done.
Total 18 (delta 3), reused 13 (delta 2), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote:
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote:
remote:     - Push cannot contain secrets
remote:
remote:
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 0a54bfee678dbe90960aad731f87e89fa356acc0
remote:            path: README.md:3
remote:          - commit: 1542f0f82ba411ff0c510060c0b37200f6b02271
remote:            path: README.md:8
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTVjWDlpTPJPLK8m7cixbLaF
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 8f0bbe7b1d6fdc43b4fc90ecc69c7ae1d8fc061e
remote:            path: README.md:8
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTZqeTmrv9pXlPj6u6o5wfAb
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 0a54bfee678dbe90960aad731f87e89fa356acc0
remote:            path: README.md:72
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTUjKLF0TAnqV4AKIyy6dGE1
remote:
remote:
remote:
To https://github.com/AtabekIsm/lab03.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push origin master
error: src refspec master does not match any
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git remote add origin https://github.com/AtabekIsm/lab03.git
error: remote origin already exists.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git branch -M main
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push -u origin main
Username for 'https://github.com': AtabekIsm
Password for 'https://AtabekIsm@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/AtabekIsm/lab03.git/'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ echo "# lab03" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/AtabekIsm/lab03.git
git push -u origin main
Reinitialized existing Git repository in /home/armvo/AtabekIsm/workspace/projects/lab03/.git/
[main e60c051] first commit
 1 file changed, 1 insertion(+)
error: remote origin already exists.
Username for 'https://github.com': AtanekIsm
Password for 'https://AtanekIsm@github.com':
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ echo "# lab03" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/AtabekIsm/lab03.git
git push -u origin main
Reinitialized existing Git repository in /home/armvo/AtabekIsm/workspace/projects/lab03/.git/
[main 2414c5e] first commit
 1 file changed, 1 insertion(+)
error: remote origin already exists.
Username for 'https://github.com': AtabekIsm
Password for 'https://AtabekIsm@github.com':
Enumerating objects: 24, done.
Counting objects: 100% (24/24), done.
Delta compression using up to 12 threads
Compressing objects: 100% (20/20), done.
Writing objects: 100% (24/24), 9.76 KiB | 9.76 MiB/s, done.
Total 24 (delta 7), reused 12 (delta 2), pack-reused 0
remote: Resolving deltas: 100% (7/7), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote:
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote:
remote:     - Push cannot contain secrets
remote:
remote:
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 0a54bfee678dbe90960aad731f87e89fa356acc0
remote:            path: README.md:3
remote:          - commit: 2414c5edc2e8eaeaa66a5c9c9eb39774339a8e27
remote:            path: README.md:3
remote:          - commit: e60c0513c78827d68796ff6fa53bba78737c808f
remote:            path: README.md:3
remote:          - commit: 1542f0f82ba411ff0c510060c0b37200f6b02271
remote:            path: README.md:8
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTVjWDlpTPJPLK8m7cixbLaF
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 8f0bbe7b1d6fdc43b4fc90ecc69c7ae1d8fc061e
remote:            path: README.md:8
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTZqeTmrv9pXlPj6u6o5wfAb
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 0a54bfee678dbe90960aad731f87e89fa356acc0
remote:            path: README.md:72
remote:          - commit: 2414c5edc2e8eaeaa66a5c9c9eb39774339a8e27
remote:            path: README.md:72
remote:          - commit: e60c0513c78827d68796ff6fa53bba78737c808f
remote:            path: README.md:72
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/AtabekIsm/lab03/security/secret-scanning/unblock-secret/2wgqTUjKLF0TAnqV4AKIyy6dGE1
remote:
remote:
remote:
To https://github.com/AtabekIsm/lab03.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git clone https://github.com/${GITHUB_USERNAME}/lab02.git projects/lab03
Cloning into 'projects/lab03'...
remote: Enumerating objects: 3008, done.
remote: Counting objects: 100% (3008/3008), done.
remote: Compressing objects: 100% (2314/2314), done.
remote: Total 3008 (delta 523), reused 2996 (delta 517), pack-reused 0 (from 0)
Receiving objects: 100% (3008/3008), 13.52 MiB | 48.00 KiB/s, done.
Resolving deltas: 100% (523/523), done.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git remote remove origin
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git add CMakeLists.txt
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git commit -m"added CMakeLists.txt"
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        projects/

nothing added to commit but untracked files present (use "git add" to track)
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push origin master
error: src refspec master does not match any
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git add
Nothing specified, nothing added.
hint: Maybe you wanted to say 'git add .'?
hint: Turn this message off by running
hint: "git config advice.addEmptyPathspec false"
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git add projects/lab03/
warning: adding embedded git repository: projects/lab03
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint:   git submodule add <url> projects/lab03
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint:   git rm --cached projects/lab03
hint:
hint: See "git help submodule" for more information.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ git push origin master
error: src refspec master does not match any
error: failed to push some refs to 'https://github.com/AtabekIsm/lab03.git'
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/projects/lab03$ popd
~/AtabekIsm/workspace
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ export LAB_NUMBER=03
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
Cloning into 'tasks/lab03'...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61 (from 1)
Receiving objects: 100% (91/91), 1.02 MiB | 830.00 KiB/s, done.
Resolving deltas: 100% (41/41), done.
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ mkdir reports/lab${LAB_NUMBER}
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace$ cd reports/lab${LAB_NUMBER}
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/reports/lab03$ edit REPORT.md
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/reports/lab03$ gist REPORT.md
gist: (WARNING) fread failed (command) on CGM file REPORT.md
gist: (WARNING) BEGIN METAFILE element missing
gist: (WARNING) REPORT.md is not a binary CGM, cannot open
gist> ^C
armvo@LAPTOP-V7PSSN9N:~/AtabekIsm/workspace/reports/lab03$
