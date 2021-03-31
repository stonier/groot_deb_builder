
NAME=$(shell basename ${CURDIR})
SKIP_TESTS=1
DISTRO=bionic
#DISTRO=focal

pre-download:
	wget https://raw.githubusercontent.com/stonier/vci/devel/stdeb.cfg

pre-pristine:
	rm -f stdeb.cfg

include ../Makefile-python3
