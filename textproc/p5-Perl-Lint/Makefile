# Created by: Adam Weinberger <adamw@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Perl-Lint
PORTVERSION=	0.22
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:MOZNION
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Yet another Perl source code linter

BUILD_DEPENDS=	p5-B-Keywords>=0:${PORTSDIR}/devel/p5-B-Keywords \
		p5-Compiler-Lexer>=0.22:${PORTSDIR}/devel/p5-Compiler-Lexer \
		p5-Email-Address>=0:${PORTSDIR}/mail/p5-Email-Address \
		p5-List-Flatten>=0:${PORTSDIR}/devel/p5-List-Flatten \
		p5-List-MoreUtils>=0.33:${PORTSDIR}/lang/p5-List-MoreUtils \
		p5-Path-Tiny>=0.068:${PORTSDIR}/devel/p5-Path-Tiny \
		p5-Regexp-Lexer>=0.05:${PORTSDIR}/devel/p5-Regexp-Lexer \
		p5-Scalar-List-Utils>=1.41:${PORTSDIR}/lang/p5-Scalar-List-Utils \
		p5-String-CamelCase>=0:${PORTSDIR}/textproc/p5-String-CamelCase \
		p5-Test-Deep>=0:${PORTSDIR}/devel/p5-Test-Deep
RUN_DEPENDS:=	${BUILD_DEPENDS}
TEST_DEPENDS=	p5-Text-TestBase>=0:${PORTSDIR}/textproc/p5-Text-TestBase

USES=		perl5
USE_PERL5=	modbuildtiny

.include <bsd.port.pre.mk>

.if ${PERL_LEVEL} >= 502000
TEST_DEPENDS+=	p5-Module-Pluggable>=0:${PORTSDIR}/devel/p5-Module-Pluggable
.endif

.include <bsd.port.post.mk>
