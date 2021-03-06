# $FreeBSD$

PORTNAME=	icinga2
DISTVERSIONPREFIX=	v
DISTVERSION=	2.3.4
CATEGORIES=	net-mgmt

MAINTAINER=	lme@FreeBSD.org
COMMENT=	Monitoring and management system for hosts, services and networks

LICENSE=	GPLv2

LIB_DEPENDS=	libboost_system.so:${PORTSDIR}/devel/boost-libs \
		libyajl.so:${PORTSDIR}/devel/yajl \
		libexecinfo.so:${PORTSDIR}/devel/libexecinfo # for better debugging
RUN_DEPENDS=	${LOCALBASE}/bin/bash:${PORTSDIR}/shells/bash

USE_GITHUB=	yes
GH_ACCOUNT=	icinga

USES=		alias bison cmake
USE_LDCONFIG=	yes

USE_RC_SUBR=	${PORTNAME}

OPTIONS_DEFINE=		DOCS
OPTIONS_MULTI=		BACKEND
OPTIONS_MULTI_BACKEND=	MYSQL PGSQL
OPTIONS_RADIO=		PLUGINS
OPTIONS_RADIO_PLUGINS=	MONPLUGINS NAGPLUGINS

OPTIONS_DEFAULT=	MYSQL PGSQL MONPLUGINS

MONPLUGINS_RUN_DEPENDS=	${LOCALBASE}/libexec/nagios/check_nagios:${PORTSDIR}/net-mgmt/monitoring-plugins
NAGPLUGINS_RUN_DEPENDS=	${LOCALBASE}/libexec/nagios/check_nagios:${PORTSDIR}/net-mgmt/nagios-plugins

MYSQL_CMAKE_ON=	-DICINGA2_WITH_MYSQL:BOOL=true
PGSQL_CMAKE_ON=	-DICINGA2_WITH_PGSQL:BOOL=true

ICINGA2USER?=	icinga
ICINGA2GROUP?=	icinga
USERS=		${ICINGA2USER}
GROUPS=		${ICINGA2GROUP}

LOCALSTATEDIR?=	/var
ICINGA2LOGDIR?=	/var/log/${PORTNAME}

CMAKE_ARGS+=	-DICINGA2_USER=${ICINGA2USER} \
		-DICINGA2_GROUP=${ICINGA2GROUP} \
		-DICINGA2_COMMAND_USER=${ICINGA2USER} \
		-DICINGA2_COMMAND_GROUP=${ICINGA2USER} \
		-DICINGA2_PLUGINDIR=${LOCALBASE}/libexec/nagios \
		-DCMAKE_INSTALL_SYSCONFDIR=${PREFIX}/etc \
		-DCMAKE_INSTALL_LOCALSTATEDIR=${LOCALSTATEDIR} \
		-DCMAKE_INSTALL_MANDIR=${MANPREFIX}/man \

SUB_LIST=	ICINGA2LOGDIR=${ICINGA2LOGDIR} \
		ICINGA2USER=${ICINGA2USER} \
		ICINGA2GROUP=${ICINGA2GROUP} \
		WWWGRP=${WWWGRP}

# Config files with references to "Linux"
LINUX_CONFIG=	groups.conf services.conf hosts.conf

MYSQL_USE=	mysql=yes
PGSQL_USES=	pgsql

OPTIONS_SUB=	yes

.include <bsd.port.options.mk>
.if ${OSVERSION} < 1000033
BUILD_DEPENDS+=	flex>=2.5.31:${PORTSDIR}/textproc/flex
CMAKE_ARGS+=	-DFLEX_EXECUTABLE:STRING=${LOCALBASE}/bin/flex
CXXFLAGS+=	-I${LOCALBASE}/include/flex
.endif

post-patch:
.for f in ${LINUX_CONFIG}
	${REINPLACE_CMD} 's,[Ll]inux,FreeBSD,g' ${WRKSRC}/etc/icinga2/conf.d/${f}
.endfor

pre-install:
	${FIND} ${WRKSRC}/etc -type f -name "*.conf" -exec ${MV} {} {}.sample \;
	${FIND} ${WRKSRC}/etc/icinga2/scripts -type f -name "*.sh" \
		-exec ${MV} {} {}.sample \;

.include <bsd.port.mk>
