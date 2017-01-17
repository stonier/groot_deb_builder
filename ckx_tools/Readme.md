
# CKX Tools

## ROS Dependencies

Dropped the ros repo dependnecies in the stdeb.cfg so it can build on the ppa. The
alternative is to build up all of the underlying dependencies (rospkg, vcstools,
wstool, osrf_common etc) and that's a pain. Lots of breakages everywhere.

## Tests

These also break it for some reason, so ckx tools setup.py has these commented out

