#
# Copyright (C) 2011-2020 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libmediainfo
PKG_VERSION:=20.03
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://mediaarea.net/download/source/libmediainfo/$(PKG_VERSION)
PKG_HASH:=bacb0cd84c74d631c05fc9ce817fd7ccefae9cb8a9a9a979dec51240ca164d2e

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

PKG_BUILD_DEPENDS:=libzen

PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk

define Package/libmediainfo
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Mediainfo support library
	URL:=http://mediaarea.net/
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/libmediainfo/description
 libmediainfo - used by mediainfo.
endef

CONFIGURE_PATH:=Project/GNU/Library

CONFIGURE_ARGS += \
	--enable-static \
	--disable-shared

MAKE_PATH:=$(CONFIGURE_PATH)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/opt/include $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/include/MediaInfo $(1)/opt/include
	$(CP) $(PKG_INSTALL_DIR)/opt/include/MediaInfoDLL $(1)/opt/include
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libmediainfo.a $(1)/opt/lib
endef

$(eval $(call BuildPackage,libmediainfo))
