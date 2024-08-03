#
# Copyright (C) 2014-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nss-map
PKG_RELEASE:=7
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/nss-map
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=@IPV6 +kmod-ip6-tunnel +libubox +libubus +iptables-mod-conntrack-extra +kmod-qca-nat46 +kmod-qca-nss-drv-map-t
  TITLE:=MAP-E/MAP-T and Lightweight 4over6 configuration support
  MAINTAINER:=Hans Dedecker <dedeckeh@gmail.com>
  PROVIDES:=map-t
endef

define Package/nss-map/description
 Provides support for MAP-E (RFC7597), MAP-T (RFC7599) and
 Lightweight 4over6 (RFC7596) in /etc/config/network.
 MAP combines address and port translation with the tunneling
 of IPv4 packets over an IPv6 network
endef

define Package/nss-map/install
	$(INSTALL_DIR) $(1)/lib/netifd/proto
	$(INSTALL_BIN) ./files/map.sh $(1)/lib/netifd/proto/map.sh
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mapcalc $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,nss-map))
# $(eval $(call Package,nss-map))
