include $(TOPDIR)/rules.mk

PKG_NAME:=simple-dict-server
PKG_RELEASE:=5.1
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-06-01
PKG_SOURCE_VERSION:=7472da6610af50c851b4d52ace26c4c1a2af9a0f
PKG_SOURCE_URL:=https://github.com/fumiama/simple-dict-server.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-dict-server
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread +libspb +libsmd5
  TITLE:=simple-dict-server
  MAINTAINER:=fumiama
endef

define Package/simple-dict-server/description
 simple-dict-server
endef

define Package/simple-dict-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/simple-dict-server $(1)/usr/bin/
endef

define Package/simple-dict-server/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/simple-dict-server
	chmod 6755 /usr/bin/simple-dict-server
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-dict-server/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "#/usr/bin/simple-dict-server -d 8000 1 /home/nobody/dict.sp /home/nobody/cfg.sp 2>&1 > /dev/null" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-dict-server/postrm
	#!/bin/sh
	sed -i '/simple-dict-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-dict-server))
