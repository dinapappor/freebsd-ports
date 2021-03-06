# Created by: Sutra Zhou <zhoushuqun@gmail.com>
# $FreeBSD$

PORTNAME=	mod_auth_openid
PORTVERSION=	0.8
DISTVERSIONPREFIX=	v
CATEGORIES=	www
PKGNAMEPREFIX=	${APACHE_PKGNAMEPREFIX}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Authentication module for the Apache 2 webserver with OpenID

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libopkele.so:${PORTSDIR}/devel/libopkele \
		libsqlite3.so:${PORTSDIR}/databases/sqlite3

USE_GITHUB=	yes
GH_ACCOUNT=	bmuller

PLIST_FILES=	${APACHEMODDIR}/mod_auth_openid.so

USE_APACHE=	22+
USES=		autoreconf cpe gmake libtool pkgconfig
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-pcre=${LOCALBASE}

CPE_VENDOR=	findingscience

CFLAGS+=	-I${LOCALBASE}/include -I/usr/include/openssl

post-patch:
	@${REINPLACE_CMD} -e 's|$${APXS} -i|$${APXS} -S LIBEXECDIR=${STAGEDIR}${PREFIX}/${APACHEMODDIR} -i|' \
		${WRKSRC}/src/Makefile.am

pre-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/${APACHEMODDIR}

.include <bsd.port.mk>
