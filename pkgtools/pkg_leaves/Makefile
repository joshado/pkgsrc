# $NetBSD: Makefile,v 1.4 2009/04/09 00:48:12 joerg Exp $

DISTNAME=	pkg_leaves-1.2
CATEGORIES=	pkgtools
MASTER_SITES=	# empty
DISTFILES=	# empty

MAINTAINER=	joerg@NetBSD.org
COMMENT=	Print leaf packages

PKG_DESTDIR_SUPPORT=	user-destdir

WRKSRC=		${WRKDIR}
NO_BUILD=	yes
USE_LANGUAGES=	# none

# Set SCRIPT_SUBST to substitute "@VARIABLE@" with "value"
SUBST_CLASSES+=	vars
SUBST_STAGE.vars=	do-configure
SUBST_FILES.vars=	pkg_leaves
SUBST_VARS.vars=	PKG_INFO_CMD PKG_DBDIR SH

INSTALLATION_DIRS=	bin

do-extract:
	cd ${FILESDIR} && cp pkg_leaves ${WRKSRC}/

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/pkg_leaves ${DESTDIR}${PREFIX}/bin

.include "../../mk/bsd.pkg.mk"
