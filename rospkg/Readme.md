## Preparation

* Get the stdeb.cfg file and tweak that (esp. Build-Depends).

```
wget https://raw.githubusercontent.com/ros-infrastructure/rospkg/master/stdeb.cfg
```

* Set `SKIP_TESTS=1` because it doesn't install test files into the source package


## Problems

* PPA runs du_auto_test which bombs because test files are not in the source package

```
======================================================================
ERROR: test_rospkg_distro.test_load_distro_bad_data
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
  File "/<<PKGBUILDDIR>>/.pybuild/pythonX.Y_2.7/build/test/test_rospkg_distro.py", line 261, in test_load_distro_bad_data
    load_distro(p)
  File "rospkg/distro.py", line 194, in load_distro
    raise ResourceNotFound('%s (%s)' % (str(e), source_uri))
ResourceNotFound: unknown url type: /<<PKGBUILDDIR>>/.pybuild/pythonX.Y_2.7/build/test/rosdistro/bad1.rosdistro (/<<PKGBUILDDIR>>/.pybuild/pythonX.Y_2.7/build/test/rosdistro/bad1.rosdistro)
```
