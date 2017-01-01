# INSTALL_PREFIX=/opt/snorriheim
SOURCE_VERSION=0.1.1
VERSION=${SOURCE_VERSION}
REPOSITORY_NAME=groot_icons
REPOSITORY_URL=https://github.com/stonier/${REPOSITORY_NAME}
TARBALL=${REPOSITORY_NAME}-${SOURCE_VERSION}.tar.gz
PACKAGE_NAME=$(subst _,-,${REPOSITORY_NAME})

help:
	@echo "Targets"
	@echo ""
	@echo "  pristine: cleans all temporaries and source tarballs"
	@echo "  clean   : cleans only temporaries"
	@echo "  download: downloads the source tarball"
	@echo "  build   : generates an unsigned source pkg & deb in ./build [req: download]"
	@echo "  sign    : signs a source package                            [req: build]"
	@echo "  upload  : sends it over to the ppa                          [req: sign]"
	@echo "  release : build, sign, upload                               [req: download]"

clean:
	@echo " - Cleaning the build temporaries"
	rm -rf build

pristine: clean
	@echo " - Cleaning downloads"
	rm -f ${TARBALL}

download: pristine
	wget -O ${TARBALL} ${REPOSITORY_URL}/archive/${SOURCE_VERSION}.tar.gz

build: clean
	@mkdir -p build
	@tar -xzf ${TARBALL} 
	@mv ${REPOSITORY_NAME}-${SOURCE_VERSION} build/${PACKAGE_NAME}-${VERSION}
	@cd build; tar -czf ${PACKAGE_NAME}_${VERSION}.orig.tar.gz ${PACKAGE_NAME}-${VERSION}
	@cp -r debian build/${PACKAGE_NAME}-${VERSION}
	@cd build/${PACKAGE_NAME}-${VERSION}; dpkg-buildpackage -us -uc -sa

sign:
	cd build/${PACKAGE_NAME}-${VERSION}/debian; debuild -S -sa

upload:
	cd build; dput ppa:d-stonier/snorriheim ${PACKAGE_NAME}_*_source.changes

release: build sign upload

# this vendor=override is broken...just clears the 'ubuntu1' default
changelog:
	dch -i --distribution=xenial --urgency=low --increment --vendor=override
