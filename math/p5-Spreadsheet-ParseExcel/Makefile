# $NetBSD: Makefile,v 1.26 2011/08/16 22:32:57 wiz Exp $
#

DISTNAME=	Spreadsheet-ParseExcel-0.59
PKGNAME=	p5-${DISTNAME}00
CATEGORIES=	math perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Spreadsheet/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://search.cpan.org/dist/Spreadsheet-ParseExcel/
COMMENT=	Perl module to get information from an Excel file
LICENSE=	${PERL5_LICENSE}

PKG_DESTDIR_SUPPORT=	user-destdir

DEPENDS+=	p5-Crypt-RC4-[0-9]*:../../security/p5-Crypt-RC4
DEPENDS+=	p5-Digest-Perl-MD5-[0-9]*:../../security/p5-Digest-Perl-MD5
DEPENDS+=	p5-OLE-Storage_Lite>=0.19:../../devel/p5-OLE-Storage_Lite
DEPENDS+=	p5-IO-stringy>=0:../../devel/p5-IO-stringy

USE_LANGUAGES=	# empty
PERL5_PACKLIST=	auto/Spreadsheet/ParseExcel/.packlist

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
