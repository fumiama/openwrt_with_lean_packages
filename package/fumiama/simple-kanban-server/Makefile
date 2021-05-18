include $(TOPDIR)/rules.mk

PKG_NAME:=simple-kanban-server
PKG_RELEASE:=1.4.1
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-kanban-server
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread +libspb
  TITLE:=simple-kanban-server
  MAINTAINER:=fumiama
endef

define Package/simple-kanban-server/description
 simple-kanban-server
endef

define Package/simple-kanban-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/simple-kanban-server $(1)/usr/bin/
endef

define Package/simple-kanban-server/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/simple-kanban-server
	chmod 4755 /usr/bin/simple-kanban-server
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-kanban-server/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "#/usr/bin/simple-kanban-server -d 12315 1 /home/nobody/kanban /home/nobody/data /home/nobody/cfg.sp 2>&1 > /dev/null" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-kanban-server/postrm
	#!/bin/sh
	sed -i '/simple-kanban-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-kanban-server))
