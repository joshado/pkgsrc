# $NetBSD: Makefile,v 1.3 2011/08/14 14:14:46 obache Exp $
#

DISTNAME=	Net-Server-SS-PreFork-0.05
PKGNAME=	p5-${DISTNAME}
PKGREVISION=	2
CATEGORIES=	net perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Net/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://search.cpan.org/dist/Net-Server-SS-PreFork/
COMMENT=	Hot-deployable variant of Perl 5 module Net::Server::PreFork
LICENSE=	${PERL5_LICENSE}

PKG_DESTDIR_SUPPORT=	user-destdir
PERL5_MODULE_TYPE=	Module::Install

USE_LANGUAGES=		# empty
PERL5_PACKLIST=		auto/Net/Server/SS/PreFork/.packlist

BUILD_DEPENDS+=	p5-HTTP-Server-Simple-[0-9]*:../../www/p5-HTTP-Server-Simple
BUILD_DEPENDS+=	p5-libwww-[0-9]*:../../www/p5-libwww
BUILD_DEPENDS+=	p5-Test-TCP>=0.06:../../net/p5-Test-TCP
DEPENDS+=	p5-Net-Server-[0-9]*:../../net/p5-Net-Server
DEPENDS+=	p5-Server-Starter>=0.02:../../sysutils/p5-Server-Starter

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
