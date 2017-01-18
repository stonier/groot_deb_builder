
## Preparation

Make sure you get the stdeb for this package ('make stdeb)' as it is not included in
the pip download.

* Get the stdeb.cfg file and tweak that (esp. Build-Depends).

```
wget https://raw.githubusercontent.com/vcstools/vcstools/master/stdeb.cfg
```

* Set `SKIP_TESTS=1` because it doesn't install test files into the source package

