# $NetBSD: Makefile,v 1.21 2010/01/22 22:30:05 tonio Exp $
#

DISTNAME=	ctags-5.8
PKGNAME=	ex${DISTNAME}
CATEGORIES=	devel
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=ctags/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://ctags.sourceforge.net/
COMMENT=	Exuberant (feature-filled) tagfile generator for vi, emacs and clones

PKG_INSTALLATION_TYPES=	overwrite pkgviews
PKG_DESTDIR_SUPPORT=	user-destdir

GNU_CONFIGURE=		yes
CONFIGURE_ARGS+=	--enable-macro-patterns
CONFIGURE_ARGS+=	--with-readlib
CONFIGURE_ARGS+=	--enable-custom-config=${PKG_SYSCONFDIR}/ctags.conf

CPPFLAGS+=		-DETAGS="\"exetags\""
# Makefile ignores CPPFLAGS
CFLAGS+=		${CPPFLAGS}

SUBST_CLASSES+=		man
SUBST_STAGE.man=	post-patch
SUBST_FILES.man=	ctags.1
SUBST_SED.man=		-e 's|^ctags \\-|exctags \\-|'
SUBST_SED.man+=		-e 's|fBctags|fBexctags|g'
SUBST_SED.man+=		-e 's|fBetags|fBexetags|g'
SUBST_SED.man+=		-e 's|"ctags|"exctags|g'
SUBST_SED.man+=		-e 's|"etags|"exetags|g'
SUBST_SED.man+=		-e 's|/usr/local|${LOCALBASE}|g'

SUBST_CLASSES+=		rename
SUBST_STAGE.rename=	post-patch
SUBST_FILES.rename=	c.c eiffel.c general.h lregex.c lua.c main.c \
			options.c parse.c routines.c
SUBST_SED.rename=	-e 's|__unused__|__unused_|g'

INSTALL_MAKE_FLAGS+=	prefix=${DESTDIR}${PREFIX} \
			mandir=${DESTDIR}${PREFIX}/${PKGMANDIR}

.include "../../mk/bsd.pkg.mk"
