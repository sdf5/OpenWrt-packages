#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libcap-ng-dev
PKG_VERSION:=2.25
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/stevegrubb/libcap-ng.git
PKG_SOURCE_DATE:=2018-02-07
#commit number
PKG_SOURCE_VERSION:=0218de0793c1135bb3a58d8b00b32d8a3cedaeb9

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/libcap-ng-dev
	TITLE:=Linux capabilities library
	SECTION:=libs
	CATEGORY:=Libraries
	URL:=https://github.com/stevegrubb/libcap-ng
endef

define Build/Configure
	( cd $(PKG_BUILD_DIR); ./autogen.sh )
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcap-ng.a $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcap-ng.so* $(1)/usr/lib/
endef

define Package/libcap-ng-dev/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libcap-ng.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libcap-ng-dev))
