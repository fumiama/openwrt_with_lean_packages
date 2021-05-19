include $(TOPDIR)/rules.mk

PKG_NAME:=simple-dict-server
PKG_RELEASE:=4.0
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-05-19
PKG_SOURCE_VERSION:=bfc06ff7448dd31e877babf4cf0782c85f06c611
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
  DEPENDS:=+libpthread +libspb
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
	chmod 4755 /usr/bin/simple-dict-server
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-dict-server/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "#/usr/bin/simple-dict-server -d 8000 1 /home/nobody/dict.sp /home/nobody/cfg.sp 2>&1 > /tmp/simple-dict-server.log" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-dict-server/postrm
	#!/bin/sh
	sed -i '/simple-dict-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-dict-server))
