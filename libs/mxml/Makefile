#
# Copyright (C) 2010 Tobias Schneider
# Copyright (C) 2007 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mxml
PKG_VERSION:=2.8
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.msweet.org/files/project3/
PKG_FIXUP:=autoreconf
PKG_MD5SUM:=d85ee6d30de053581242c4a86e79a5d2

include $(INCLUDE_DIR)/package.mk

define Package/mxml
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=mini-xml
  URL:=http://www.minixml.org/
endef

define Package/mxml/description
  A small xml library.
endef

TARGET_CFLAGS += $(FPIC)

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-shared \
		--enable-static \
	)
endef

define Build/InstallDev
	mkdir -p $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/mxml.h $(1)/usr/include/
	mkdir -p $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libmxml.so* $(1)/usr/lib/
	mkdir -p $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_BUILD_DIR)/mxml.pc $(1)/usr/lib/pkgconfig/
endef

define Package/mxml/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libmxml.so*  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,mxml))
