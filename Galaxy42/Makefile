
include $(TOPDIR)/rules.mk

PKG_NAME:=Galaxy42
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sdf5/galaxy42.git
PKG_SOURCE_DATE:=2016-12-29
#commit number or branch or tag name
PKG_SOURCE_VERSION:=OpenWrt

#PKG_MAINTAINER:=Nazwa <email>
PKG_LICENSE:=Antinet / Galaxy / Yedino - Licence
PKG_LICENSE_FILES:=LICENCE.txt

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

HOST_CFLAGS+= -DBACKWARD_SYSTEM_UNKNOWN
HOST_CPPFLAGS+= -DBACKWARD_SYSTEM_UNKNOWN
HOST_LDFLAGS+= -latomic

TARGET_CFLAGS+= -DBACKWARD_SYSTEM_UNKNOWN
TARGET_CPPFLAGS+= -DBACKWARD_SYSTEM_UNKNOWN
TARGET_LDFLAGS+= -latomic

HOST_CFLAGS+= -DOPEN_WRT
HOST_CPPFLAGS+= -DOPEN_WRT

TARGET_CFLAGS+= -DOPEN_WRT
TARGET_CPPFLAGS+= -DOPEN_WRT

define Package/Galaxy42
        SECTION:=Galaxy
	CATEGORY:=Galaxy
	DEPENDS:=+libcap-ng-dev +libsodium +boost +boost-system +boost-filesystem +boost-program_options +boost-thread +boost-date_time +libatomic +kmod-tun
	TITLE:=Galaxy
	URL:=https://github.com/yedino/galaxy42
endef

define Package/Galaxy42/description

endef

define Build/InstallDev

endef

define Package/Galaxy42/install
	#languages
	(cd $(PKG_BUILD_DIR) && ./contrib/tools/galaxy42-lang-update-all)
	$(INSTALL_DIR) $(1)/usr/share/locale/
	$(CP) $(PKG_BUILD_DIR)/share/locale/* $(1)/usr/share/locale/
	
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tunserver.elf $(1)/usr/bin/
endef

$(eval $(call BuildPackage,Galaxy42))





