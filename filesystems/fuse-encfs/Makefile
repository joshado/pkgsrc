# $NetBSD: Makefile,v 1.7 2010/01/17 12:02:16 wiz Exp $
#

DISTNAME=	encfs-1.2.0-2
PKGNAME=	fuse-${DISTNAME:S/-2/.2/}
PKGREVISION=	2
CATEGORIES=	filesystems
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=encfs/}
EXTRACT_SUFX=	.tgz

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://www.arg0.net/encfs
COMMENT=	FUSE Encrypted Filesystem

PKG_DESTDIR_SUPPORT=	user-destdir

WRKSRC=		${WRKDIR}/${DISTNAME:S/-2//}
GNU_CONFIGURE=	yes
USE_TOOLS+=	autoconf gmake pkg-config
USE_LANGUAGES=	c c++

.include "../../mk/bsd.prefs.mk"

.if ${OPSYS} == "NetBSD"
CPPFLAGS+=	-D_NETBSD_SOURCE
.endif

.include "../../devel/librlog/buildlink3.mk"
.include "../../security/openssl/buildlink3.mk"
.include "../../mk/fuse.buildlink3.mk"
.include "../../mk/pthread.buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
