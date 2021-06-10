This repository contains static builds of Qt for Windows that are compatible with Bitcoin Core.

*Please be aware this download is NOT an officially sanctioned Bitcoin Core distribution and is provided for developer convenience. It should NOT be used for builds that will be used in a production environment or with real funds.*

Note: To build using a specific version of Visual Studio install the `build tools` package from [here](https://docs.microsoft.com/en-us/visualstudio/releases/2019/history#installing-an-earlier-release).

Note: To check which version of Visual Studio Appveyor is currently using see [here](https://www.appveyor.com/docs/windows-images-software/).

Note: Optimise flags have been deliberately removed from QMAKE flags. This is an attempt to avoid ABI compatibility issues between minor updates of the msvc compiler.
See https://docs.microsoft.com/en-us/cpp/porting/binary-compat-2015-2017?view=msvc-160.

### Qt5.12.11
Build steps
````
Download source from https://download.qt.io/official_releases/qt/5.12/5.12.11/single/qt-everywhere-src-5.12.11.zip
Modify c:\dev\qt-everywhere-src-5.12.11\qt-everywhere-src-5.12.11\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += -Zi -MT
QMAKE_CFLAGS_DEBUG      = -Zi -MTd
Open x64 Native Tools Command Prompt for VS 2019
cd c:\Dev\qt-everywhere-src-5.12.11\qt-everywhere-src-5.12.11\
mkdir build
cd build
..\configure -developer-build -confirm-license -debug-and-release -opensource -platform win32-msvc -opengl desktop -no-shared -static -no-static-runtime -mp -qt-zlib -qt-pcre -qt-libpng -ltcg -make libs -make tools -no-libjpeg -nomake examples -no-compile-examples -no-dbus -no-libudev -no-icu -no-gtk -no-opengles3 -no-angle -no-sql-sqlite -no-sql-odbc -no-sqlite -no-libudev -no-vulkan -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns -nomake tests -no-openssl -prefix C:\Qt5.12.11_x64_static_vs2019_16101
nmake
nmake install
````

### Qt5.12.10
Build steps
````
Download source from https://download.qt.io/official_releases/qt/5.12/5.12.11/single/qt-everywhere-src-5.12.11.zip
Modify c:\dev\qt-everywhere-src-5.12.11\qt-everywhere-src-5.12.11\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += -Zi -MT
QMAKE_CFLAGS_DEBUG      = -Zi -MTd
Open x64 Native Tools Command Prompt for VS 2019
cd c:\Dev\qt-everywhere-src-5.12.11\qt-everywhere-src-5.12.11\
mkdir build
cd build
..\configure -developer-build -confirm-license -debug-and-release -opensource -platform win32-msvc -opengl desktop -no-shared -static -no-static-runtime -mp -qt-zlib -qt-pcre -qt-libpng -ltcg -make libs -make tools -no-libjpeg -nomake examples -no-compile-examples -no-dbus -no-libudev -no-icu -no-gtk -no-opengles3 -no-angle -no-sql-sqlite -no-sql-odbc -no-sqlite -no-libudev -no-vulkan -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns -nomake tests -no-openssl -prefix C:\Qt5.12.11_x64_static_vs2019_16101
nmake
nmake install

shasum -a 256 /mnt/c/temp/Qt5.12.11_x64_static_vs2019_16101.zip > sha256sum
gpg --clearsign -u aaron@sipsorcery.com -a sha256suml
````

### Qt5.12.6
Build steps
````
Download source from https://download.qt.io/official_releases/qt/5.12/5.12.6/single/qt-everywhere-src-5.12.6.zip
Modify qt-everywhere-src-5.12.6\qt-everywhere-src-5.12.6\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += -Zi -MT
QMAKE_CFLAGS_DEBUG      = -Zi -MTd
Open x64 Native Tools Command Prompt for VS 2019
mkdir qtbuild
cd qtbuild
..\configure -debug-and-release -opensource -platform win32-msvc -opengl desktop -no-shared -no-static-runtime -mp -c++std c++11 -confirm-license -ltcg -static -make libs -make tools -optimized-tools -pch -qt-libpng -qt-pcre -qt-harfbuzz -system-zlib -no-compile-examples -no-angle -no-cups -no-dbus -no-egl -no-eglfs -no-freetype -no-gif -no-glib -no-gtk -no-icu -no-ico -no-iconv -no-kms -no-linuxfb -no-libjpeg -no-libproxy -no-libudev -no-mtdev -no-opengles3 -no-openssl -no-openvg -no-reduce-relocations -no-sctp -no-sql-db2 -no-sql-ibase -no-sql-oci -no-sql-tds -no-sql-mysql -no-sql-odbc -no-sql-psql -no-sql-sqlite -no-sql-sqlite2 -no-sqlite -no-system-proxies -no-use-gold-linker -nomake examples -nomake tests -no-feature-bearermanagement -no-feature-colordialog -no-feature-commandlineparser -no-feature-concurrent -no-feature-dial -no-feature-dtls -no-feature-ftp -no-feature-http -no-feature-image_heuristic_mask -no-feature-keysequenceedit -no-feature-lcdnumber -no-feature-networkdiskcache -no-feature-networkproxy -no-feature-pdf -no-feature-printdialog -no-feature-printer -no-feature-printpreviewdialog -no-feature-printpreviewwidget  -no-feature-sessionmanager -no-feature-socks5 -no-feature-sqlmodel -no-feature-statemachine -no-feature-syntaxhighlighter -no-feature-textodfwriter -no-feature-topleveldomain -no-feature-udpsocket -no-feature-undocommand -no-feature-undogroup -no-feature-undostack -no-feature-undoview -no-feature-vnc -no-feature-whatsthis -no-feature-wizard -no-feature-xml -skip qt3d -skip qtactiveqt -skip qtandroidextras -skip qtcanvas3d -skip qtcharts -skip qtconnectivity -skip qtdatavis3d -skip qtdeclarative -skip qtdoc -skip qtgamepad -skip qtgraphicaleffects -skip qtimageformats -skip qtlocation -skip qtmacextras -skip qtmultimedia -skip qtnetworkauth -skip qtpurchasing -skip qtquickcontrols -skip qtquickcontrols2 -skip qtscript -skip qtscxml -skip qtsensors -skip qtserialbus -skip qtserialport -skip qtspeech -skip qttools -skip qtvirtualkeyboard -skip qtwayland -skip qtwebchannel -skip qtwebengine -skip qtwebglplugin -skip qtwebsockets -skip qtwebview -skip qtx11extras -skip qtxmlpatterns -IC:\tools\vcpkg\installed\x64-windows-static\include -LC:\tools\vcpkg\installed\x64-windows-static\lib -prefix C:\Qt5.12.6_x64_static_vs2019
nmake
nmake install
````

### Qt5.9.8
Build steps
````
Download source from https://download.qt.io/official_releases/qt/5.9/5.9.8/single/
Modify qt-everywhere-opensource-src-5.9.8\qt-everywhere-opensource-src-5.9.8\qtbase\mkspecs\common\msvc-desktop.conf and set:
QMAKE_CFLAGS_RELEASE    = -MT
QMAKE_CFLAGS_RELEASE_WITH_DEBUGINFO += -Zi -MT
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
