include $(TOPDIR)/rules.mk

PKG_NAME:=simple-dict-server
PKG_RELEASE:=3.1
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-dict-server
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread
  TITLE:=simple-dict-server
  MAINTAINER:=fumiama
endef

define Package/simple-dict-server/description
 simple-dict-server
endef

define Package/simple-dict-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/simple-dict-server $(1)/usr/bin/
endef

define Package/simple-dict-server/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/simple-dict-server
	chmod 4755 /usr/bin/simple-dict-server
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-dict-server/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "/usr/bin/simple-dict-server -d 8000 1 /home/nobody/dict 2>&1 > /tmp/simple-dict-server.log" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-dict-server/postrm
	#!/bin/sh
	sed -i '/simple-dict-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-dict-server))
