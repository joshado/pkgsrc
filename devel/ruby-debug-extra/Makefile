# $NetBSD: Makefile,v 1.2 2011/06/19 15:27:19 taca Exp $

DISTNAME=	ruby-debug-extra-0.10.4
PKGNAME=	${RUBY_PKGPREFIX}-${DISTNAME:S/ruby-//}
CATEGORIES=	devel
MASTER_SITES=	http://rubyforge.org/frs/download.php/73086/

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://rubyforge.org/projects/ruby-debug/
COMMENT=	Emacs support and the Reference Manual for ruby-debug
LICENSE=	2-clause-bsd

PKG_DESTDIR_SUPPORT=	user-destdir

RUBY_VERSION_SUPPORTED= 18
GNU_CONFIGURE=	YES
INFO_FILES=	YES

DOCS=		ruby-debug.info ruby-debug.pdf
INFO=		rdebug-emacs.info ruby-debug.info

MAKE_FLAGS+=	DESTDIR=${DESTDIR:Q}
MAKE_FLAGS+=	prefix=${PREFIX:Q}
MAKE_FLAGS+=	EMACS=${EMACS_BIN:Q}

INSTALLATION_DIRS+=	${PKGMANDIR}/man1 ${PKGINFODIR} ${RUBY_DOC}/ruby-debug

post-install:
	${INSTALL_MAN} ${WRKSRC}/doc/rdebug.1 \
		${DESTDIR}${PREFIX}/${PKGMANDIR}/man1
.for f in ${INFO}
	${INSTALL_DATA} ${WRKSRC}/doc/${f} ${DESTDIR}${PREFIX}/${PKGINFODIR}
.endfor
.for f in ${DOCS}
	${INSTALL_DATA} ${WRKSRC}/doc/${f} \
		${DESTDIR}${PREFIX}/${RUBY_DOC}/ruby-debug
.endfor

.include "../../editors/emacs/modules.mk"
.include "../../lang/ruby/modules.mk"
.include "../../mk/bsd.pkg.mk"
