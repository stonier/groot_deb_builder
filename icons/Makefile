NAME=groot-icons
INSTALL_PREFIX=/opt/snorriheim/media/icons
MAJOR=0
MINOR=1
PATCH=0
VERSION=${MAJOR}.${MINOR}.${PATCH}

clean:
	@echo " - Clearing the workspace"
	@rm -rf ${NAME}-* build

sources: clean
	@mkdir -p ${NAME}-${VERSION}
	@cp -r sources/* ${NAME}-${VERSION}
	@cp -r files/* ${NAME}-${VERSION}
	@mkdir -p build/deb_dist
	@echo " - Creating build/deb_dist/${NAME}-${VERSION}.orig.tar.gz"
	@tar -czf build/${NAME}-${VERSION}.tar.gz ${NAME}-${VERSION}
	#@tar -czf deb_dist/${NAME}-${VERSION}.orig.tar.gz ${NAME}-${VERSION}
	#tar -cvJf deb_dist/${NAME}-${VERSION}.debian.tar.xz debian 

# dpkg-source -b ../groot-icons-0.1.0

dummy:
