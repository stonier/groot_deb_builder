
NAME=$(shell basename ${CURDIR})
SKIP_TESTS=1
DISTRO=focal

pre-download:
	rm -f stdeb.cfg
	wget https://raw.githubusercontent.com/stonier/groot_rocker_extensions/devel/stdeb.cfg

pre-pristine:
	rm -f stdeb.cfg

include ../Makefile-python3
