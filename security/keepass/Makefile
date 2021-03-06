# Created by: Ben Woods <woodsb02@gmail.com>
# $FreeBSD$

PORTNAME=	keepass
PORTVERSION=	2.29
CATEGORIES=	security
MASTER_SITES=	SF/${PORTNAME}/KeePass%202.x/${PORTVERSION}
DISTNAME=	KeePass-${PORTVERSION}-Source

MAINTAINER=	woodsb02@gmail.com
COMMENT=	Light-weight and easy-to-use password manager

LICENSE=	GPLv2 # or later

BUILD_DEPENDS=	icotool:${PORTSDIR}/graphics/icoutils
LIB_DEPENDS=	libgcrypt.so:${PORTSDIR}/security/libgcrypt \
		libgdiplus.so:${PORTSDIR}/x11-toolkits/libgdiplus
RUN_DEPENDS=	xdotool:${PORTSDIR}/x11/xdotool \
		xsel:${PORTSDIR}/x11/xsel

EXTRACT_AFTER_ARGS=	-d ${WRKDIR}/${DISTNAME}

USES=		mono zip
INSTALLS_ICONS=	yes
SUB_FILES=	${PORTNAME}.sh

DESKTOP_ENTRIES="KeePass" \
		"${COMMENT}" \
		"${PORTNAME}" \
		"keepass.sh" \
		"Utility;" \
		true

do-build:
	# Extract icons
	(cd ${WRKSRC} && ${LOCALBASE}/bin/icotool -x KeePass/KeePass.ico)
	# Prepare build
	(cd ${WRKSRC}/Build && ${SH} PrepMonoDev.sh)
	# Do build
	(cd ${WRKSRC} && \
		${SETENV} ${MAKE_ENV} ${LOCALBASE}/bin/xbuild /t:KeePass /p:Configuration=Release)

do-install:
	@${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME}.sh ${STAGEDIR}${PREFIX}/bin
	${INSTALL_DATA} ${WRKSRC}/Build/KeePass/Release/KeePass.exe ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/Ext/KeePass.config.xml ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/Ext/KeePass.exe.config ${STAGEDIR}${DATADIR}
	@(cd ${WRKSRC}/Ext && ${COPYTREE_SHARE} XSL ${STAGEDIR}${DATADIR})
.for size in 16 32 48 256
	@${MKDIR} ${STAGEDIR}${LOCALBASE}/share/icons/hicolor/${size}x${size}/apps
	${INSTALL_DATA} ${WRKSRC}/KeePass_*_${size}x${size}x32.png \
		${STAGEDIR}${LOCALBASE}/share/icons/hicolor/${size}x${size}/apps/keepass.png
.endfor

.include <bsd.port.mk>
