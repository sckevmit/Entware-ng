#
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=popt
PKG_VERSION:=1.16
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://rpm5.org/files/popt/
PKG_HASH:=e728ed296fe9f069a0e005003c3d6b2dde3d9cad453422a10d6558616d304cc8
PKG_LICENSE:=MIT

PKG_FIXUP:=autoreconf
PKG_REMOVE_FILES:=autogen.sh aclocal.m4

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS += $(FPIC)

define Package/libpopt
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=A command line option parsing library
  URL:=http://rpm5.org/files/popt/
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-shared \
		--enable-static \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/opt/include
	$(CP) $(PKG_INSTALL_DIR)/opt/include/popt.h $(1)/opt/include/
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libpopt.{a,so*} $(1)/opt/lib/
	$(INSTALL_DIR) $(1)/opt/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/pkgconfig/popt.pc $(1)/opt/lib/pkgconfig/
endef

define Package/libpopt/install
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libpopt.so.* $(1)/opt/lib/
endef

$(eval $(call BuildPackage,libpopt))

