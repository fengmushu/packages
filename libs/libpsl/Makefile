#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libpsl
PKG_VERSION:=0.20.2
PKG_RELEASE:=3

PKG_MAINTAINER:=W. Michael Petullo <mike@flyn.org>

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/rockdaboot/libpsl/releases/download/$(PKG_NAME)-$(PKG_VERSION)/
PKG_HASH:=f8fd0aeb66252dfcc638f14d9be1e2362fdaf2ca86bde0444ff4d5cc961b560f

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/libpsl
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=C library to handle the Public Suffix List
  URL:=https://github.com/rockdaboot/libpsl
  DEPENDS:=+libidn2 +libunistring $(INTL_DEPENDS)
endef

define Package/libpsl/description
  C library to handle the Public Suffix List
endef

CONFIGURE_ARGS += \
	--disable-gtk-doc-html \
	--disable-man \
	--disable-rpath

define Build/InstallDev
	$(INSTALL_DIR) \
		$(1)/usr/lib \
		$(1)/usr/include

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/* \
		$(1)/usr/lib/
endef

define Package/libpsl/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpsl))
