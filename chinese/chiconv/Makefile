# Created by: buganini@gmail.com
# $FreeBSD$

PORTNAME=	chiconv
PORTVERSION=	11.1
CATEGORIES=	chinese converters

MAINTAINER=	buganini@gmail.com
COMMENT=	Auto chinese encoding converter

LICENSE=	ISCL

LIB_DEPENDS=	libbsdconv.so:${PORTSDIR}/converters/bsdconv

USE_GITHUB=	yes
GH_ACCOUNT=	buganini

MAKE_ARGS=	PREFIX=${PREFIX}

PLIST_FILES=	bin/chiconv

.include <bsd.port.mk>
