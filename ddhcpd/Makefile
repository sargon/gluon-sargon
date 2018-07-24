include $(TOPDIR)/rules.mk

PKG_NAME:=ddhcpd
PKG_VERSION:=2018-06-28
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sargon/ddhcpd
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=4f6c088a7032224535fd41090cc6a4c12673efbe
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

TARGET_CFLAGS += -DLOG_LEVEL=20

include $(TOPDIR)/../package/gluon.mk

define Package/ddhcpd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=ddhcpd
endef

define Package/ddhcpd/description
 distributed dhcp server
endef

define Build/Compile
        CFLAGS="$(TARGET_CFLAGS)" BUILD_DIR="$(BUILD_DIR)" $(MAKE) -C $(PKG_BUILD_DIR) $(TARGET_CONFIGURE_OPTS)
endef

define Package/ddhcpd/install
	$(CP) ./files/* $(1)
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpd  $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpdctl $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ddhcpd))
