# $NetBSD: Makefile,v 1.16 2012/03/03 00:13:01 wiz Exp $

PKG_DESTDIR_SUPPORT=	user-destdir

.include "../../meta-pkgs/xfce4/Makefile.common"

XFCE4_VERSION=	0.2.16

DISTNAME=	mousepad-${XFCE4_VERSION}
PKGNAME=	xfce4-mousepad-${XFCE4_VERSION}
PKGREVISION=	8
CATEGORIES=	editors
COMMENT=	Xfce text editor

.include "../../sysutils/desktop-file-utils/desktopdb.mk"
.include "../../x11/libxfce4gui/buildlink3.mk"
.include "../../mk/pthread.buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
