# $NetBSD: Makefile,v 1.50 2012/06/07 13:48:18 ryoon Exp $
#

DISTNAME=	nspr-${NSPR_RELEASE}
PKGNAME=	nspr-4.9.3.1 # some reason
NSPR_RELEASE=	4.9.1
CATEGORIES=	devel
MASTER_SITES=	${MASTER_SITE_MOZILLA_ALL:=nspr/releases/v${NSPR_RELEASE}/src/}

MAINTAINER=	tnn@NetBSD.org
HOMEPAGE=	http://www.mozilla.org/projects/nspr/index.html
COMMENT=	Platform-neutral API for system level and libc like functions

PKG_DESTDIR_SUPPORT=	user-destdir
CHECK_PORTABILITY_SKIP+=${MOZILLA_DIR}security/nss/tests/libpkix/libpkix.sh
CHECK_PORTABILITY_SKIP+=${MOZILLA_DIR}security/nss/tests/multinit/multinit.sh
CHECK_PORTABILITY_SKIP+=${MOZILLA_DIR}js/src/configure
CHECK_PORTABILITY_SKIP+=${MOZILLA_DIR}configure

WRKSRC=			${WRKDIR}/${DISTNAME}/mozilla

GNU_CONFIGURE=		yes
GNU_CONFIGURE_LIBSUBDIR=nspr
CONFIGURE_DIRS=		nsprpub

USE_TOOLS+=		autoconf213 gmake perl
REPLACE_PERL+=		nsprpub/pr/src/misc/compile-et.pl

CONFIGURE_ARGS+=	--disable-debug
CONFIGURE_ARGS+=	--with-pthreads
CONFIGURE_ENV+=		LIBRUNPATH=${PREFIX:Q}/lib/nspr

.include "../../mk/bsd.prefs.mk"

SUBST_CLASSES+=			nspr-config
SUBST_STAGE.nspr-config=	pre-configure
SUBST_MESSAGE.nspr-config=	Fixing nspr-config run path
SUBST_FILES.nspr-config=	nsprpub/config/nspr-config.in
SUBST_SED.nspr-config=		-e 's|-L$$libdir|"${COMPILER_RPATH_FLAG}$$libdir -L$$libdir"|g'

.if ${OBJECT_FMT} == "ELF"
SO_SUFFIX=		so
.elif ${OBJECT_FMT} == "Mach-O"
SO_SUFFIX=		dylib
.else
SO_SUFFIX=		so.1.0
.endif
PLIST_SUBST+=		SO_SUFFIX=${SO_SUFFIX:Q}

PLIST_VARS+=		sun4u_32
# see nsprpub/pr/src/md/unix/Makefile.in
# for the bit about 32-bit sun4u machines installing an extra file.
# That is why we have this specific test and modify the PLIST
.if ${OPSYS} == "SunOS"
.  if defined(ABI) && ${ABI} == "64"
CONFIGURE_ARGS+=	--enable-64bit
.  else
HW_CLASS!=	${UNAME} -m
.    if ${HW_CLASS} == "sun4u"
PLIST.sun4u_32=                yes
.    endif
.  endif
.endif

.if ${OPSYS} == "Linux"
.  if defined(ABI) && ${ABI} == "64"
CONFIGURE_ARGS+=	--enable-64bit
.  endif
.endif

.if ${OPSYS} == "Darwin" && exists(/Developer/Headers/FlatCarbon)
BUILDLINK_PASSTHRU_DIRS+=	Developer/Headers/FlatCarbon
.endif

pre-configure:
	cd ${WRKSRC}/nsprpub && autoconf

post-build:
	set -e; ( \
	  ${ECHO} "Name: NSPR"; \
	  ${ECHO} "Description: The Netscape Portable Runtime";	\
	  ${ECHO} "Version: ${NSPR_RELEASE}";			\
	  ${ECHO} "Cflags: -I${PREFIX}/include/nspr";		\
	  ${ECHO} "Libs: -L${PREFIX}/lib/nspr"			\
	    "${COMPILER_RPATH_FLAG}${PREFIX}/lib/nspr"		\
	    "-lplds4 -lplc4 -lnspr4 "${BUILDLINK_LIBS.pthread:Q};	\
	) > ${WRKDIR}/nspr.pc

INSTALLATION_DIRS+=	lib/pkgconfig

post-install:
	${INSTALL_DATA} ${WRKDIR}/nspr.pc ${DESTDIR}${PREFIX}/lib/pkgconfig

.include "../../mk/pthread.buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
