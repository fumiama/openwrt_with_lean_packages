include $(TOPDIR)/rules.mk

PKG_NAME:=simple-dict-server
PKG_RELEASE:=1
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-dict-server
  SECTION:=utils
  CATEGORY:=Server
  TITLE:=simple-dict-server
endef

define Package/simple-dict-server/description
 simple-dict-server
endef

define Package/simple-dict-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/simple-dict-server $(1)/usr/bin/
endef

$(eval $(call BuildPackage,simple-dict-server))
