# Created by: Ernst de Haan <znerd@FreeBSD.org>
# $FreeBSD$

PORTNAME=	xinclude-task
PORTVERSION=	0.2
PORTREVISION=	2
CATEGORIES=	textproc java
MASTER_SITES=	http://people.freebsd.org/~znerd/xinclude-task/
PKGNAMEPREFIX=	ant-

MAINTAINER=	ports@FreeBSD.org
COMMENT=	XInclude task for Jakarta Ant

LICENSE=	NONE

DEPRECATED=	unknown license
EXPIRATION_DATE=	2018-08-15

BUILD_DEPENDS=	${JAVALIBDIR}/xincluder.jar:textproc/xincluder

USE_JAVA=	yes
JAVA_VERSION=	1.6+
USE_ANT=	yes
NO_ARCH=	yes

ALL_TARGET=	jar apidocs
PORTDOCS=	*
MAKE_ENV=	CLASSPATH=${JAVALIBDIR}/xincluder.jar

PLIST_FILES=	%%JAVAJARDIR%%/${PORTNAME}.jar

OPTIONS_DEFINE=	DOCS

do-install:
	@${MKDIR} ${JAVAJARDIR}
	${INSTALL_DATA} ${WRKSRC}/build/${PORTNAME}.jar ${STAGEDIR}${JAVAJARDIR}/

do-install-DOCS-on:
	cd ${WRKSRC}/build/apidocs && ${COPYTREE_SHARE} . ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
