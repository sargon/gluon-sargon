include $(TOPDIR)/rules.mk

PKG_NAME:=ddhcpd
PKG_VERSION:=2018-06-28

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sargon/ddhcpd
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=ef0c682408c7494ca24b0be959700c3c4c079862
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

TARGET_CFLAGS += -DLOG_LEVEL=20 

include $(INCLUDE_DIR)/package.mk

define Package/ddhcpd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=ddhcpd
endef

define Package/ddhcpd/description
 distributed dhcp server
endef

define Package/ddhcpd/install
	$(CP) ./files/* $(1)
	mkdir -p $(1)/usr/sbin/
	$(CP) $(PKG_BUILD_DIR)/ddhcpd  $(1)/usr/sbin/
	$(CP) $(PKG_BUILD_DIR)/ddhcpdctl $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ddhcpd))
