# $NetBSD: Makefile,v 1.3 2012/06/14 07:45:20 sbd Exp $

MODNAME=		dom
PKGREVISION=		2
CATEGORIES+=		textproc
COMMENT=		PHP5 extension for DOM support

CONFLICTS=	php-dom-[0-9]*

PKG_DESTDIR_SUPPORT=	user-destdir

CONFIGURE_ARGS+=	--enable-${MODNAME}
CONFIGURE_ARGS+=	--with-libxml-dir=${BUILDLINK_PREFIX.libxml2}

.include "../../lang/php/ext.mk"
#.include "../../devel/zlib/buildlink3.mk"
.include "../../textproc/libxml2/buildlink3.mk"
#.include "../../textproc/libxslt/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
