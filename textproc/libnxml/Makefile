# $NetBSD: Makefile,v 1.3 2011/04/22 13:42:10 obache Exp $
#

DISTNAME=	libnxml-0.18.3
PKGREVISION=	2
CATEGORIES=	textproc
MASTER_SITES=	http://www.autistici.org/bakunin/libnxml/

MAINTAINER=	kamel.derouiche@gmail.com
HOMEPAGE=	http://www.autistici.org/bakunin/libnxml/doc/
COMMENT=	C library for parsing, writing and creating XML files or streams
LICENSE=	gnu-lgpl-v2.1

PKG_DESTDIR_SUPPORT=	user-destdir

GNU_CONFIGURE=	yes
USE_LIBTOOL=	yes
USE_TOOLS+=	pkg-config
USE_LANGUAGES=		c c++

PKGCONFIG_OVERRIDE+=	nxml.pc.in

.include "../../www/curl/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
