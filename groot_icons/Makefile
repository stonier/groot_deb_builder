# INSTALL_PREFIX=/opt/snorriheim
VERSION=0.2.0
REPOSITORY_NAME=$(shell basename ${CURDIR})
REPOSITORY_URL=https://github.com/stonier/${REPOSITORY_NAME}
TARBALL=${REPOSITORY_NAME}-${VERSION}.tar.gz
ORIG_TARBALL=${PACKAGE_NAME}_${VERSION}.orig.tar.gz
PACKAGE_NAME=$(subst _,-,${REPOSITORY_NAME})

help:
	@echo "Targets"
	@echo ""
	@echo "  pristine : cleans all temporaries and source tarballs"
	@echo "  clean    : cleans only temporaries"
	@echo "  download : downloads/builds an orig.tar.gz source tarball"
	@echo "  changelog: edit the changelog"
	@echo "  build    : generates an unsigned source pkg & deb in ./build [req: download]"
	@echo "  sign     : signs a source package                            [req: build]"
	@echo "  upload   : sends it over to the ppa                          [req: sign]"
	@echo "  release  : build, sign, upload                               [req: download]"

clean:
	rm -rf build

pristine: clean
	rm -f ${TARBALL}
	rm -f ${ORIG_TARBALL}

# make sure to use -n with gzip so filename and timestamp is not archived
# otherwise ppa will complain it's getting a different original 
download: pristine
	wget -O ${TARBALL} ${REPOSITORY_URL}/archive/${VERSION}.tar.gz
	@tar -xzf ${TARBALL}
	@mv ${REPOSITORY_NAME}-${VERSION} ${PACKAGE_NAME}-${VERSION}
	@tar -cvf ${PACKAGE_NAME}_${VERSION}.orig.tar ${PACKAGE_NAME}-${VERSION}
	@gzip -n ${PACKAGE_NAME}_${VERSION}.orig.tar
	@rm ${TARBALL}
	@rm -rf ${PACKAGE_NAME}-${VERSION}

build: clean
	@mkdir -p build
	@tar -xzf ${ORIG_TARBALL} -C build
	@ln -s ../${ORIG_TARBALL} build/${ORIG_TARBALL}
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
