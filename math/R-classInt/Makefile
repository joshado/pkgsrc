# $NetBSD: Makefile,v 1.6 2012/04/15 16:00:01 brook Exp $

CATEGORIES=	math
MASTER_SITES=	${MASTER_SITE_R_CRAN:=contrib/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	${R_HOMEPAGE_BASE}/genetics/
COMMENT=	Package for choosing univariate class intervals for graphics
LICENSE=	gnu-gpl-v2

R_PKGNAME=	classInt
R_PKGVER=	0.1-17

USE_LANGUAGES=	c fortran

DEPENDS+=	R-e1071>=1.6:../../math/R-e1071

.include "../../math/R/Makefile.extension"
.include "../../mk/bsd.pkg.mk"
