# $NetBSD: Makefile,v 1.36 2012/06/14 07:43:18 sbd Exp $

DISTNAME=	libfwbuilder-4.1.3
PKGREVISION=	6
CATEGORIES=	security net
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=fwbuilder/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://www.fwbuilder.org/
COMMENT=	Firewall Builder API
LICENSE=	gnu-gpl-v2

PKG_DESTDIR_SUPPORT=	user-destdir

USE_LANGUAGES=		c c++
USE_LIBTOOL=		yes
USE_TOOLS+=		aclocal autoconf automake gmake
GNU_CONFIGURE=		yes
CONFIGURE_ARGS+=	--without-distcc

INSTALL_MAKE_FLAGS+=	INSTALL_ROOT=${DESTDIR}

pre-configure:
	cd ${WRKSRC} && libtoolize -c -f -i && aclocal && autoconf

.include "../../devel/zlib/buildlink3.mk"
.include "../../net/net-snmp/buildlink3.mk"
.include "../../textproc/libxml2/buildlink3.mk"
.include "../../textproc/libxslt/buildlink3.mk"
.include "../../x11/qt4-libs/buildlink3.mk"
.include "../../x11/qt4-tools/buildlink3.mk"
.include "../../mk/pthread.buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
