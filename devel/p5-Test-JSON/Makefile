# Created by: Lars Thegler <lth@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Test-JSON
PORTVERSION=	0.11
PORTREVISION=	1
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-
DISTNAME=	${PORTNAME}-${DISTVERSION:C/0$//}

MAINTAINER=	lth@FreeBSD.org
COMMENT=	Test JSON data

RUN_DEPENDS=	p5-Test-Differences>=0.47:${PORTSDIR}/devel/p5-Test-Differences \
		p5-Test-Tester>=0.10.7:${PORTSDIR}/devel/p5-Test-Tester \
		p5-JSON-Any>=1.20:${PORTSDIR}/converters/p5-JSON-Any
BUILD_DEPENDS:=	${RUN_DEPENDS}

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>
