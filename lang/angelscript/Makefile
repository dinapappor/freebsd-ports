# Created by: Veniamin Gvozdikov <vg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	angelscript
PORTVERSION=	2.29.0
CATEGORIES=	lang
MASTER_SITES=	http://www.angelcode.com/angelscript/sdk/files/
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	vg@FreeBSD.org
COMMENT=	AngelCode Scripting Library

LICENSE=	ZLIB

MAKEFILE=	makefile
MAKE_ARGS=	LOCAL=${STAGEDIR}${PREFIX}
USES=		gmake zip compiler:c++0x
USE_LDCONFIG=	yes

WRKSRC=		${WRKDIR}/sdk/angelscript/projects/gnuc/

PLIST_FILES=	include/angelscript.h \
		lib/libangelscript.a

.include <bsd.port.mk>
