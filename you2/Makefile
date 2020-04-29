TARGET = you2
VERSION = 0.1
CC = xcrun -sdk iphoneos clang -arch armv7 -arch arm64 -arch arm64e -miphoneos-version-min=9.0
LDID = ldid
GO_EASY_ON_ME=1
.PHONY: all clean

all: clean postinst
	sh make-you2.sh
	mkdir org.brandonplank.you2_$(VERSION)_iphoneos-arm
	mkdir org.brandonplank.you2_$(VERSION)_iphoneos-arm/DEBIAN
	cp control org.brandonplank.you2_$(VERSION)_iphoneos-arm/DEBIAN
	mv postinst org.brandonplank.you2_$(VERSION)_iphoneos-arm/DEBIAN
	mkdir org.brandonplank.you2_$(VERSION)_iphoneos-arm/usr
	mkdir org.brandonplank.you2_$(VERSION)_iphoneos-arm/usr/bin
	mv Build/Debug-iphoneos/you2 org.brandonplank.you2_$(VERSION)_iphoneos-arm/usr/bin
	$(LDID) -Sentitlements.xml org.brandonplank.you2_$(VERSION)_iphoneos-arm/usr/bin/you2
	dpkg -b org.brandonplank.you2_$(VERSION)_iphoneos-arm

postinst: clean
	$(CC) postinst.c -o postinst
	strip postinst
	$(LDID) -Sentitlements.xml postinst

clean:
	rm -rf org.brandonplank.you2_* postinst you2/.theos
