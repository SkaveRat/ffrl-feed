#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

# Package content copyright (C) 
#      2011 2011 Darkeye <postfach@martinmichel.info>
#      2011 egon0 <ms@resonar.de>
#      2011 Frank Lanitz <frank@frank.uvena.de>
#      2011 Martin Michel <darkeye@seestern.(none)>
#      2011 frlan <frank@frank.uvena.de>
# 2011-2012 egon_ffj <egon@freifunk-jena.de>
# 2011-2012 Jan Huwald <jh@sotun.de>
# 2011-2012 Freifunk Rheinland e. V. <http://www.freifunk-rheinland.net/>
# 2011-2012 LCB01 <lcb01@fnordeingang.de>
#      2012 Kai de Haan <skaverat@funlynx.de>


include $(TOPDIR)/rules.mk

PKG_NAME:=ffrl-webservice
PKG_VERSION:=0.1.0
PKG_RELEASE:=4
PKG_REV:=eb2afeca552f3a4e5aeff5a02ad67e04241c0347

PKG_SOURCE:=$(PKG_NAME)-$(PKG_REV).tar.gz
PKG_MD5SUM:=always-use-git
PKG_SOURCE_URL:=git://github.com/SkaveRat/webservice.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=git

include $(INCLUDE_DIR)/package.mk

define Package/ffrl-webservice
  SECTION:=base
  CATEGORY:=Utilities
  SUBMENU:=Freifunk Rheinland
  PKGARCH:=all
  DEFAULT:=n
  TITLE:=Freifunk Rheinland e. V. Webservice
  MAINTAINER:=Linus Broich <lcb01@lcb01.de>
  URL:=https://freifunk-rheinland.net
  DEPENDS:=+uhttpd +ffrl-fsm-inetable
endef

define Package/ffrl-webservice/description
  Dem Freifunknutzer wird bei der ersten Einwahl ins Freifunk eine Splash-Seite
  Präsentiert. Möchte er ins Internet gelangen muss er den Bedingungen
  zustimmen. Außerdem erhält der Nutzer auf diesen Webseiten die wichtigsten
  Informationen über den Freifunk.
endef

define Build/Compile
endef

define Package/ffrl-webservice/install
	$(INSTALL_DIR) $(1)/etc/config $(1)/www $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sbin/splash_sync $(1)/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/etc/splash.sh $(1)/etc/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/etc/config/splash_users $(1)/etc/config
	$(CP) -ap $(PKG_BUILD_DIR)/www/* $(1)/www
	mkdir -p $(1)/CONTROL
	$(INSTALL_BIN) ./ipkg/ffrl-webservice.postinst $(1)/CONTROL/postinst
	$(INSTALL_BIN) ./ipkg/ffrl-webservice.postrm $(1)/CONTROL/postrm
endef

$(eval $(call BuildPackage,ffrl-webservice))
