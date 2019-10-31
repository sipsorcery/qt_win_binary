This repository contains static builds of Qt for Windows that are compatible with Bitcoin Core.

*Please be aware this download is NOT an officially sanctioned Bitcoin Core distribution and is provided for developer convenience. It should NOT be used for builds that will be used in a production environment or with real funds.*


### Qt5.9.8
Build steps
````
Download source from https://download.qt.io/official_releases/qt/5.9/5.9.8/single/
Modify qt-everywhere-opensource-src-5.9.8\qt-everywhere-opensource-src-5.9.8\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = $$QMAKE_CFLAGS_OPTIMIZE -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += $$QMAKE_CFLAGS_OPTIMIZE -Zi -MT
QMAKE_CFLAGS_DEBUG      = -Zi -MTd
Open x64 Native Tools Command Prompt for VS 2019
mkdir qtbuild
cd qtbuild
..\qt-everywhere-opensource-src-5.9.8\qt-everywhere-opensource-src-5.9.8\configure -developer-build -confirm-license -debug-and-release -opensource -platform win32-msvc -opengl desktop -no-shared -static -no-static-runtime -mp -qt-zlib -qt-pcre -qt-libpng -ltcg -make libs -make tools -no-libjpeg -nomake examples -no-compile-examples -no-dbus -no-libudev -no-qml-debug -no-icu -no-gtk -no-opengles3 -no-angle -no-sql-sqlite -no-sql-odbc -no-sqlite -no-libudev -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns -nomake tests -no-openssl -IC:\tools\vcpkg\installed\x64-windows-static\include -LC:\tools\vcpkg\installed\x64-windows-static\lib -prefix C:\Qt5.9.8_x64_static_vs2019
nmake
nmake install
````

### Qt5.9.7
Build steps
````
Modify Qtv5.9.7_src\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = $$QMAKE_CFLAGS_OPTIMIZE -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += $$QMAKE_CFLAGS_OPTIMIZE -Zi -MT
QMAKE_CFLAGS_DEBUG      = -Zi -MTd
Open x64 Native Tools Command Prompt for VS 2017
..\Qtv5.9.7_src\configure -developer-build -confirm-license -debug-and-release -opensource -platform win32-msvc -opengl desktop -no-shared -static -no-static-runtime -mp -qt-zlib -qt-pcre -qt-libpng -qt-libjpeg -ltcg -make libs -make tools -nomake examples -no-compile-examples -no-dbus -no-libudev -no-qml-debug -no-icu -no-gtk -no-opengles3 -no-angle -no-sql-sqlite -no-sql-odbc -no-sqlite -no-libudev -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns -nomake tests -openssl-linked -IC:\Dev\github\vcpkg\installed\x64-windows-static\include -LC:\Dev\github\vcpkg\installed\x64-windows-static\lib OPENSSL_LIBS="-llibeay32 -lssleay32 -lgdi32 -luser32 -lwsock32 -ladvapi32" -prefix C:\Qt5.9.7_ssl_x64_static_vs2017
nmake
nmake install
````
