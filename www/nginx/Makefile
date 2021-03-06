# $NetBSD: Makefile,v 1.22 2012/04/21 10:32:47 imil Exp $

DISTNAME=		nginx-1.0.15
CATEGORIES=		www
MASTER_SITES=		http://nginx.org/download/
DISTFILES=		${DEFAULT_DISTFILES}

MAINTAINER=		joerg@NetBSD.org
HOMEPAGE=		http://nginx.org/
COMMENT=		Lightweight HTTP server and mail proxy server
LICENSE=		2-clause-bsd

PKG_DESTDIR_SUPPORT=	user-destdir
.include "../../mk/bsd.prefs.mk"

NGINX_USER?=		nginx
NGINX_GROUP?=		nginx
NGINX_DATADIR?=		${VARBASE}/db/nginx
NGINX_LOGDIR?=		${VARBASE}/log/nginx
NGINX_PIDDIR?=		${VARBASE}/run

BUILD_DEFS+=		NGINX_DATADIR NGINX_LOGDIR NGINX_PIDDIR VARBASE

PKG_USERS_VARS+=	NGINX_USER
PKG_GROUPS_VARS+=	NGINX_GROUP
PKG_GROUPS=		${NGINX_GROUP}
PKG_USERS=		${NGINX_USER}:${NGINX_GROUP}

PKG_GECOS.${NGINX_USER}=NGINX server user
PKG_HOME.${NGINX_USER}=	${NGINX_DATADIR}
PKG_SHELL.${NGINX_USER}=${NOLOGIN}

USE_PKGLOCALEDIR=	yes
HAS_CONFIGURE=		yes
CONFIGURE_ARGS+=	--user=${NGINX_USER}
CONFIGURE_ARGS+=	--group=${NGINX_GROUP}
CONFIGURE_ARGS+=	--with-ld-opt=-L${PREFIX}/lib\ -Wl,-R${PREFIX}/lib
CONFIGURE_ARGS+=	--prefix=${PREFIX}
CONFIGURE_ARGS+=	--sbin-path=${PREFIX}/sbin
CONFIGURE_ARGS+=	--conf-path=${PKG_SYSCONFDIR}/nginx.conf
CONFIGURE_ARGS+=	--pid-path=${NGINX_PIDDIR}/nginx.pid
CONFIGURE_ARGS+=	--lock-path=${NGINX_DATADIR}/nginx.lock
CONFIGURE_ARGS+=	--error-log-path=${NGINX_LOGDIR}/error.log
CONFIGURE_ARGS+=	--http-log-path=${NGINX_LOGDIR}/access.log
CONFIGURE_ARGS+=	--http-client-body-temp-path=${NGINX_DATADIR}/client_body_temp
CONFIGURE_ARGS+=	--http-proxy-temp-path=${NGINX_DATADIR}/proxy_temp
CONFIGURE_ARGS+=	--http-fastcgi-temp-path=${NGINX_DATADIR}/fstcgi_temp

.include "../../mk/bsd.prefs.mk"

PKG_SYSCONFSUBDIR=	nginx

.include "options.mk"

EGDIR=			${PREFIX}/share/examples/nginx
EGFILES+=		fastcgi.conf fastcgi_params koi-utf koi-win \
			mime.types nginx.conf win-utf

.for file in ${EGFILES}
CONF_FILES+=	${EGDIR}/conf/${file} ${PKG_SYSCONFDIR}/${file}
.	if !empty(PKG_OPTIONS:Mnaxsi)
CONF_FILES+=	${EGDIR}/conf/naxsi_core.rules
CONF_FILES+=	${PKG_SYSCONFDIR}/naxsi_core.rules
.	endif
.endfor

RCD_SCRIPTS=		nginx

INSTALLATION_DIRS=	${PKGMANDIR}/man8 sbin share/examples/nginx/conf \
			share/examples/nginx/html
MAKE_DIRS+=		${NGINX_PIDDIR}
OWN_DIRS=		${NGINX_LOGDIR}
OWN_DIRS_PERMS+=	${NGINX_DATADIR} ${NGINX_USER} ${NGINX_GROUP} 0700

BUILD_TARGET=		build

SUBST_CLASSES+=		paths
SUBST_STAGE.paths=	pre-configure
SUBST_FILES.paths=	conf/nginx.conf
SUBST_SED.paths=	-e 's,%%PKG_SYSCONFDIR%%,${PKG_SYSCONFDIR},g'
SUBST_SED.paths+=	-e 's,%%NGINX_LOGDIR%%,${NGINX_LOGDIR},g'
SUBST_SED.paths+=	-e 's,%%NGINX_PIDDIR%%,${NGINX_PIDDIR},g'
SUBST_SED.paths+=	-e 's,%%NGINX_USER%%,${NGINX_USER},g'
SUBST_SED.paths+=	-e 's,%%NGINX_GROUP%%,${NGINX_GROUP},g'

MESSAGE_SUBST+=		NGINX_LOGDIR=${NGINX_LOGDIR}
MESSAGE_SUBST+=		NGINX_PIDDIR=${NGINX_PIDDIR}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/objs/nginx ${DESTDIR}${PREFIX}/sbin/nginx
.for file in ${EGFILES}
	${INSTALL_DATA} ${WRKSRC}/conf/${file} ${DESTDIR}${EGDIR}/conf/${file}
.endfor
	${INSTALL_DATA} ${WRKSRC}/html/50x.html ${DESTDIR}${EGDIR}/html/50x.html
	${INSTALL_DATA} ${WRKSRC}/html/index.html ${DESTDIR}${EGDIR}/html/index.html
	${INSTALL_MAN} ${WRKSRC}/man/nginx.8 ${DESTDIR}${PREFIX}/${PKGMANDIR}/man8
.if !empty(PKG_OPTIONS:Mnaxsi)
	${INSTALL_DATA} ${WRKDIR}/${NAXSI}/naxsi_config/naxsi_core.rules ${DESTDIR}${EGDIR}/conf
.endif


.include "../../devel/zlib/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
