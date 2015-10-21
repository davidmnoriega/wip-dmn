# $NetBSD$

DISTNAME=	0.8.14
PKGNAME=        ${PYPKGPREFIX}-fail2ban-${DISTNAME:S/python-/-/}
CATEGORIES=	security net python
#MASTER_SITES=	https://github.com/fail2ban/fail2ban/archive/
MASTER_SITES=	${MASTER_SITE_GITHUB:=fail2ban/fail2ban/archive/}

MAINTAINER=	davidmnoriega@gmail.com
HOMEPAGE=	http://www.fail2ban.org/
COMMENT=	Daemon to ban hosts that cause multiple authentication errors 
LICENSE=	gnu-gpl-v2

WRKSRC=		${WRKDIR}/fail2ban-${DISTNAME}
ETCDIR=		${PREFIX}/etc
USE_LANGUAGES=	# none

PYTHON_VERSIONED_DEPENDENCIES= dns

PYSETUPINSTALLARGS+=       --install-lib=${PREFIX}/${PYSITELIB}

FILES=		fail2ban-client \
		fail2ban-regex \
		client/configreader.py \
		setup.py

SUBST_CLASSES+=	fix-paths
SUBST_STAGE.fix-paths=	post-patch
SUBST_MESSAGE.fix-paths=	Fixing etc path
SUBST_FILES.fix-paths=	${FILES}
SUBST_SED.fix-paths=	-e 's,/etc/fail2ban,${ETCDIR}/fail2ban,g'

MAKE_DIRS+=	/var/run/fail2ban

SMF_NAME=	fail2ban
SMF_METHODS=	fail2ban


.include "../../lang/python/distutils.mk"
.include "../../lang/python/application.mk"
.include "../../lang/python/versioned_dependencies.mk"
.include "../../mk/bsd.pkg.mk"
