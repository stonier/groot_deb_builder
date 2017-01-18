## Preparation

* Get the stdeb.cfg file and tweak that (esp. Build-Depends).

```
wget https://raw.githubusercontent.com/osrf/osrf_pycommon/master/stdeb.cfg
```

* Set `SKIP_TESTS=1` because it doesn't install test files into the source package

