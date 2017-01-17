
NAME=$(shell basename ${CURDIR})
DISTRO=xenial
BUILD_OPTIONS=--extra-cfg-file stdeb.cfg

include ../Makefile-python

stdeb:
	wget --no-clobber https://raw.githubusercontent.com/vcstools/vcstools/master/stdeb.cfg

