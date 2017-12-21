include $(TOPDIR)/rules.mk

PKG_NAME:=ddhcpd
PKG_VERSION:=2016-12-27

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.toppoint.de/sargon/ddhcpd
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=cc45bcd1ab27afb5b1dd6e749ee1b56d73591289
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

TARGET_CFLAGS += -DLOG_LEVEL=20 

include $(GLUONDIR)/include/package.mk

define Package/ddhcpd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=ddhcpd
endef

define Package/ddhcpd/install
	$(CP) ./files/* $(1)
	mkdir -p $(1)/usr/sbin/
	$(CP) $(PKG_BUILD_DIR)/ddhcpd  $(1)/usr/sbin/
	$(CP) $(PKG_BUILD_DIR)/ddhcpdctl $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ddhcpd))
