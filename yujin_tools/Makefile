# uses the local stdeb.cfg
# py2dsc can also use an additional external stdeb.cfg via --extra-cfg-file
# py2dsc could alternatively use --suite here instead of stdeb.cfg

download:
	pip download yujin_tools

clean:
	rm -rf deb_dist

pristine: clean
	rm yujin_tools*.tar.gz

build: clean
	#py2dsc --extra-cfg-file stdeb.cfg yujin_tools*.tar.gz
	py2dsc yujin_tools*.tar.gz
	cd deb_dist/yujin-tools*/debian; debuild -S -sa

deb: clean
	py2dsc-deb yujin_tools*.tar.gz

upload:
	cd deb_dist; dput ppa:d-stonier/snorriheim yujin-tools_*_source.changes 
