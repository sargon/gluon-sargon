include $(TOPDIR)/rules.mk

PKG_NAME:=ddhcpd
PKG_VERSION:=2018-08-30
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sargon/ddhcpd
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=b4eb8d97237483fc7bcad662b9f855bb96566e11
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

define Build/Prepare
	$(call Gluon/Build/Prepare)
	$(CP) gluonShellDiet.sh $(PKG_BUILD_DIR)/gluonShellDiet.sh
endef

define ShellSrcDiet
	rm -rf $(2)
	$(CP) $(1) $(2)
	$(FIND) $(2) -type f | while read src; do \
		$(PKG_BUILD_DIR)/gluonShellDiet.sh "$$$$src" > "$$$$src.o"; \
		chmod $$$$(stat -c%a "$$$$src") "$$$$src.o"; \
		mv "$$$$src.o" "$$$$src"; \
	done
endef

define Build/Compile
  CFLAGS="$(TARGET_CFLAGS)" BUILD_DIR="$(BUILD_DIR)" $(MAKE) -C $(PKG_BUILD_DIR) $(TARGET_CONFIGURE_OPTS)
  $(call Gluon/Build/Compile)
  $(call ShellSrcDiet,shsrc,$(PKG_BUILD_DIR)/shdest/)
endef

define Package/ddhcpd/install
	$(Gluon/Build/Install)
	$(CP) $(PKG_BUILD_DIR)/shdest/. $(1)/
	$(CP) ./files/* $(1)
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpd  $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ddhcpdctl $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ddhcpd))


define Package/ffffm-button-bind/install
endef
