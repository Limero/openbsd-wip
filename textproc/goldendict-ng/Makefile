COMMENT =		next neneration GoldenDict
CATEGORIES =		textproc education x11

DIST_TUPLE =		github	xiaoyifang	goldendict-ng	\
				v23.09.29-MoonCake.7f0f8778	.
PKGNAME =		${DISTNAME:C/-[[:alnum:].]*$//}

# GPLv3+
PERMIT_PACKAGE =	Yes

MAINTAINER =		Klemens Nanni <kn@openbsd.org>

WANTLIB += ${COMPILER_LIBCXX} GL Qt6Concurrent Qt6Core Qt6Core5Compat
WANTLIB += Qt6Gui Qt6Multimedia Qt6Network Qt6OpenGL Qt6PrintSupport
WANTLIB += Qt6Qml Qt6QmlModels Qt6Quick Qt6Svg Qt6TextToSpeech
WANTLIB += Qt6WebChannel Qt6WebEngineCore Qt6WebEngineWidgets
WANTLIB += Qt6Widgets Qt6Xml X11 Xtst avcodec avformat avutil
WANTLIB += bz2 c fmt hunspell-1.7 iconv icudata icui18n icuuc
WANTLIB += lzma lzo2 m opencc swresample vorbis vorbisfile xapian
WANTLIB += z zim zstd

# C++17
COMPILER =		base-clang ports-gcc

MODULES =		devel/cmake \
			x11/qt6

LIB_DEPENDS =		archivers/bzip2 \
			archivers/libzim \
			archivers/lzo2 \
			archivers/xz \
			archivers/zstd \
			audio/libvorbis \
			converters/libiconv \
			converters/opencc \
			devel/fmt \
			graphics/ffmpeg \
			textproc/hunspell \
			textproc/icu4c \
			x11/qt6/qt5compat \
			x11/qt6/qtmultimedia \
			x11/qt6/qtsvg \
			x11/qt6/qtwebengine

RUN_DEPENDS =		devel/desktop-file-utils

CONFIGURE_ARGS =	-DCMAKE_DISABLE_FIND_PACKAGE_Git=ON

# ${WRKSRC}/CMakeLists.txt requires and links it unconditionally
LIB_DEPENDS +=		x11/qt6/qtspeech
#CONFIGURE_ARGS +=	-DWITH_TTS=OFF

# ${WRKSRC}/CMakeLists.txt =OFF does not require it, but
# WRKSRC}/src/ftshelpers.cc uses it unconditionally
LIB_DEPENDS +=		databases/xapian-core
#CONFIGURE_ARGS +=	-DWITH_XAPIAN=OFF

# use "-ng" suffix
CONFIGURE_ARGS +=	-DUSE_ALTERNATIVE_NAME=ON

# pick devel/fmt over bundle
CONFIGURE_ARGS +=	-DUSE_SYSTEM_FMT=ON

# unported;    Could not find EB_LIBRARY using the following names: eb
CONFIGURE_ARGS +=	-DWITH_EPWING_SUPPORT=OFF

MODCMAKE_LDFLAGS +=	-L${X11BASE}/lib

.include <bsd.port.mk>
