# Created by: Dmitry Marakasov <amdmi3@FreeBSD.org>
# $FreeBSD$

PORTNAME=	chapping
PORTVERSION=	0.43
PORTREVISION=	13
CATEGORIES=	games
MASTER_SITES=	http://forja.rediris.es/frs/download.php/760/ \
		http://mirror.amdmi3.ru/distfiles/
DISTNAME=	${PORTNAME}-${PORTVERSION}-src

MAINTAINER=	amdmi3@FreeBSD.org
COMMENT=	Turn based board football game

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		gmake tar:bzip2
USE_SDL=	sdl image gfx ttf

CXXFLAGS+=	-Wno-c++11-narrowing

WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}-source
ALL_TARGET=	linux

PLIST_FILES=	bin/${PORTNAME}
PORTDATA=	*

post-patch:
	@${REINPLACE_CMD} -e 's|make|$${MAKE}|g' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e '/^CXX=/ d; s|^SDL=.*|SDL=${SDL_CONFIG}|; \
		/\.o:/ d; /^CXXFLAGS=/ s|=-g -Wall -O2|+=|' \
		${WRKSRC}/library/Makefile ${WRKSRC}/game/Makefile
	@${REINPLACE_CMD} -e 's|menuimg/|${DATADIR}/&|; s|themes/|${DATADIR}/&|' \
		${WRKSRC}/game/*.cpp

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin/
	cd ${WRKSRC} && ${COPYTREE_SHARE} "menuimg themes" ${STAGEDIR}${DATADIR}/

.include <bsd.port.mk>
