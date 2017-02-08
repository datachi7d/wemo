include $(TOPDIR)/rules.mk

PKG_NAME:=WeMo_Insight
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/WeMo_Insight
  CATEGORY := Belkin
  SUBMENU  := Apps
  SECTION  := utils
  TITLE    := WeMo Insight App
  DEPENDS  += +libcares +libuuid +libupnp +libpjnath +libmxml +sqlite +NatClient
  DEPENDS  += +gnupg
endef

define Package/WeMo_Insight/description
	WeMo Insight primary application
endef

define Build/Prepare
endef

define Build/Compile
endef

define Package/WeMo_Insight/install
	$(CP) ./files/* $(1)/
	rm -rf $(1)/usr/include
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/include $(1)/lib
	$(CP) ./files/usr/include/* $(1)/include
	$(CP) ./files/lib/* $(1)/lib
endef

$(eval $(call BuildPackage,WeMo_Insight))

