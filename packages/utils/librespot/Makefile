# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2023 Facundo Acevedo

include $(TOPDIR)/rules.mk

PKG_NAME:=librespot
PKG_VERSION:=0.4.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/librespot-org/librespot/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=cc8cb81bdbaa5abf366170dec5e6b8c0ecf570a7cb68f04483e9f7eed338ca61

PKG_MAINTAINER:=Peter
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENCE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/librespot
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Spotify client
  DEPENDS:=$(RUST_ARCH_DEPENDS) 
  URL:=https://github.com/librespot-org/librespot
endef

define Package/librespot/description
  Spotify client. 
endef

define Package/librespot/conffiles
/etc/librespot/librespot.toml
endef

define Package/librespot/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/procs $(1)/usr/bin/librespot
	$(INSTALL_DIR) $(1)/etc/librespot
	$(INSTALL_CONF) ./files/etc/librespot/librespot.toml $(1)/etc/librespot/
endef

$(eval $(call RustBinPackage,librespot))
$(eval $(call BuildPackage,librespot))
