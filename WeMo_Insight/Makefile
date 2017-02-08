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
  DEPENDS  += +libcares +libuuid +libupnp +libpjnath +libmxml +sqlite +NatClient +libopenssl +librt +libpthread
  DEPENDS  += +gnupg
endef

define Package/WeMo_Insight/description
	WeMo Insight primary application
endef

define Build/Prepare
endef

define Build/Compile
endef

define stdlib_hack
	find $(1)/ -type f | xargs -I {} sed -i 's|libpthread.so.0|libgcc_s.so.1\x00\x00|g' {}
	find $(1)/ -type f | xargs -I {} sed -i 's|libc.so.0|libc.so\x00\x00|g' {}
	find $(1)/ -type f | xargs -I {} sed -i 's|libm.so.0|libc.so\x00\x00|g' {}
	find $(1)/ -type f | xargs -I {} sed -i 's|libdl.so.0|libc.so\x00\x00\x00|g' {}
	find $(1)/ -type f | xargs -I {} sed -i 's|librt.so.0|libc.so\x00\x00\x00|g' {}
	find $(1)/ -type f | xargs -I {} sed -i 's|libcurl.so.5|libcurl.so.4|g' {}
endef


define Package/WeMo_Insight/install
	$(CP) ./files/* $(1)/
	rm -rf $(1)/usr/include
	$(call stdlib_hack,$(1))
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/include $(1)/lib
	$(CP) ./files/usr/include/* $(1)/include
	$(CP) ./files/lib/* $(1)/lib
endef

$(eval $(call BuildPackage,WeMo_Insight))

