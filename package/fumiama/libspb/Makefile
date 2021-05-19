#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=simple-protobuf
PKG_RELEASE:=1.1
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-05-19
PKG_SOURCE_VERSION:=6db9ffe3f0500301db1b7f32a81bbae30889a9b9
PKG_SOURCE_URL:=https://github.com/fumiama/simple-protobuf.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libspb
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Simple protobuf library
  URL:=https://github.com/fumiama/simple-protobuf
endef

define Package/libspb/description
 This package contains a library for simple-* apps.
endef

define Package/libspb/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libspb.so $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/simple-protobuf
	$(CP) $(PKG_INSTALL_DIR)/usr/include/simple_protobuf.h $(1)/usr/include/simple-protobuf/
	
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libspb.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libspb))
