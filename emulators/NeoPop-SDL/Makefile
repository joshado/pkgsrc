# $NetBSD: Makefile,v 1.13 2011/01/13 13:37:35 wiz Exp $
#

DISTNAME=		NeoPop-SDL-0.2
PKGREVISION=		8
CATEGORIES=		emulators
MASTER_SITES=		http://www.nih.at/NeoPop-SDL/
EXTRACT_SUFX=		.tar.bz2

MAINTAINER=		wiz@NetBSD.org
HOMEPAGE=		http://www.nih.at/NeoPop-SDL/
COMMENT=		SNK NeoGeo Pocket emulator

PKG_DESTDIR_SUPPORT=	user-destdir

GNU_CONFIGURE=		yes
CONFIGURE_ARGS+=	--with-png=${BUILDLINK_PREFIX.png}

.include "../../devel/SDL/buildlink3.mk"
.include "../../graphics/png/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
