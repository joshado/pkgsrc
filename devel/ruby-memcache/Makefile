# $NetBSD: Makefile,v 1.4 2011/02/21 16:01:14 taca Exp $

DISTNAME=	ruby-memcache-0.1.0
PKGNAME=	${RUBY_PKGPREFIX}-${DISTNAME:S/ruby-//}
PKGREVISION=	2
CATEGORIES=	devel
MASTER_SITES=	http://rubyforge.org/frs/download.php/2484/
EXTRACT_SUFX=	.tar.bz2

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://rubyforge.org/projects/memcache/
COMMENT=	Ruby wrapper for memcache
LICENSE=	mit

PKG_DESTDIR_SUPPORT=	user-destdir

USE_RUBY_EXTCONF=	yes

.include "../../lang/ruby/modules.mk"

.include "../../devel/libmemcache/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
