# Created by: Alexandros Kosiaris <akosiaris+ports@gmail.com>
# $FreeBSD$

PORTNAME=	celery
PORTVERSION=	3.1.15
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	wg@FreeBSD.org
COMMENT=	Asynchronous task queue/job queue

LICENSE=	BSD3CLAUSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}billiard>=3.3.0.18:${PORTSDIR}/devel/py-billiard \
		${PYTHON_PKGNAMEPREFIX}pytz>=1.5:${PORTSDIR}/devel/py-pytz \
		${PYTHON_PKGNAMEPREFIX}kombu>=3.0.23:${PORTSDIR}/net/py-kombu \
		${PYTHON_PKGNAMEPREFIX}memcached>=0:${PORTSDIR}/databases/py-memcached

USES=		python
USE_PYTHON=	autoplist distutils

.include <bsd.port.mk>
