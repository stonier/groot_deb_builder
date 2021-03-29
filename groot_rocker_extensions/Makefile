
NAME=$(shell basename ${CURDIR})
SKIP_TESTS=1

pre-download:
	wget https://raw.githubusercontent.com/stonier/groot_rocker_extensions/devel/stdeb.cfg

pre-pristine:
	rm -f stdeb.cfg

include ../Makefile-python3
