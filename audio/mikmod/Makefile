# $NetBSD: Makefile,v 1.45 2012/06/04 09:29:54 wiz Exp $

DISTNAME=	mikmod-3.2.1
PKGREVISION=	3
CATEGORIES=	audio
MASTER_SITES=	http://mikmod.raphnet.net/files/

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://mikmod.raphnet.net/
COMMENT=	MOD player for UNI IT XM S3M MOD MTM STM DSM MED FAR ULT 669 files

PKG_DESTDIR_SUPPORT=	user-destdir
PKG_INSTALLATION_TYPES=	overwrite pkgviews

USE_TOOLS+=		gmake
GNU_CONFIGURE=		yes

.include "../../audio/libmikmod/buildlink3.mk"
.include "../../devel/ncurses/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
