# Created by: "Waitman Gobble" <uzimac@da3m0n8t3r.com>
# $FreeBSD$

PORTNAME=	dcraw-m
PORTVERSION=	9.22
PORTREVISION=	1
CATEGORIES=	graphics

MAINTAINER=	waitman@waitman.net
COMMENT=	Modified Decoder for RAW files from digital cameras

LICENSE=	GPLv2

LIB_DEPENDS=	libjasper.so:${PORTSDIR}/graphics/jasper \
		libjpeg.so:${PORTSDIR}/graphics/jpeg \
		liblcms2.so:${PORTSDIR}/graphics/lcms2 \
		libMagickWand-6.so:${PORTSDIR}/graphics/ImageMagick

USE_GITHUB=	yes
GH_ACCOUNT=	waitman
GH_TAGNAME=	1392579

USES=		pkgconfig

CFLAGS += 	-Wall -I${LOCALBASE}/include \
		`MagickWand-config --cflags --cppflags` \
		-DMAGICKCORE_HDRI_ENABLE=0 \
		-DMAGICKCORE_QUANTUM_DEPTH=16
LDFLAGS +=	`MagickWand-config --ldflags --libs` -lm -llcms2 -ljpeg \
		-ljasper
LIBS    +=      -L${LOCALBASE}/lib

PLIST_FILES=	bin/dcraw-m

do-build:
	( cd ${WRKSRC} ; \
	${CC} ${CFLAGS} ${LIBS} ${LDFLAGS} -o ${PORTNAME} ${PORTNAME}.c )

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin/

.include <bsd.port.mk>
