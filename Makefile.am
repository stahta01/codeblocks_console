SUBDIRS = src

ACLOCAL_AMFLAGS = -I m4

if KEEP_DLLS
ADDITIONAL_MAKE_DIST_OPTIONS = --exclude=".svn"
else
ADDITIONAL_MAKE_DIST_OPTIONS = --exclude=".svn" --exclude="*.dll"
endif

am__tar = @am__tar@ $(ADDITIONAL_MAKE_DIST_OPTIONS)

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = codeblocks.pc

# Add some files needed only when making a bundle
if DARWIN
osxbundledir = $(pkgdatadir)/osx_bundle
dist_osxbundle_DATA = bundle.sh \
					codeblocks.plist

osxbundle_iconsdir = $(osxbundledir)/icons
dist_osxbundle_icons_DATA = $(top_srcdir)/src/src/resources/icons/*.icns
endif

EXTRA_DIST = bootstrap \
		codeblocks.spec \
		codeblocks.spec.fedora \
		codeblocks.plist \
		BUGS \
		BUILD \
		COMPILERS \
		$(srcdir)/update* \
		ChangeLog.xsl \
		codeblocks.appdata.xml \
		codeblocks-contrib.metainfo.xml \
		debian

clean-zipfiles:
	find . -name "*.zip" | xargs rm -f

clean-bin:
	find . -name "*.la" | xargs rm -f
	rm -f src/src/codeblocks

all-local:
if HAVE_WX29
	cp $(top_srcdir)/debian/codeblocks-headers.install.wx30 $(top_srcdir)/debian/codeblocks-headers.install
else
	cp $(top_srcdir)/debian/codeblocks-headers.install.wx28 $(top_srcdir)/debian/codeblocks-headers.install
endif

clean-local:
	rm -f $(top_srcdir)/debian/codeblocks-headers.install

appdatadir = $(datarootdir)/appdata
dist_appdata_DATA = $(top_srcdir)/codeblocks.appdata.xml
