# $NetBSD: Makefile,v 1.11 2012/07/01 19:30:24 morr Exp $

PKGNAME=	${DISTNAME:C/-/84-plperl-/}
COMMENT=	PL/Perl procedural language for the PostgreSQL backend

PKG_DESTDIR_SUPPORT=	user-destdir

DEPENDS+=	postgresql84-server>=${PKGVERSION_NOREV}:../../databases/postgresql84-server

.include "../../databases/postgresql84/Makefile.common"

USE_TOOLS+=		perl
PERL5_CONFIGURE=	no
CONFIGURE_ARGS+=	--with-perl

BUILD_DIRS=		src/pl/plperl
BUILD_MAKE_FLAGS=	PGXS=1
MAKE_FILE=		GNUmakefile

.include "../../databases/postgresql84-client/buildlink3.mk"
.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
