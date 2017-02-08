include $(TOPDIR)/rules.mk

PKG_NAME:=WeMo_Link
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS +=  -I$(STAGING_DIR)/usr/include/upnp
TARGET_LDFLAGS += -lbelkin_nvram -lbelkin_api -L$(STAGING_DIR)/usr/lib -lz
TARGET_LDFLAGS += -lAddlInfra -lNetworkControl -lDeviceControl -lRemoteAccess
TARGET_LDFLAGS += -lWemoDB -lUPnPHndlr -lPluginHndlr
TARGET_LDFLAGS += -lsysevent -lulog -lsubdevice -lzigbee_api
TARGET_LDFLAGS += -lupnp -lthreadutil -lixml -lpthread -lssl -lcrypto
TARGET_LDFLAGS += -lcurl -lcares -lm
TARGET_LDFLAGS += -lpjnath-pc-linux-gnu -lpjlib-util-pc-linux-gnu
TARGET_LDFLAGS += -lpj-pc-linux-gnu -luuid
TARGET_LDFLAGS += -lpmortem

define Package/WeMo_Link
  CATEGORY := Belkin
  SUBMENU  := Apps
  SECTION  := utils
  TITLE    := WeMo Link App
  DEPENDS  += +libcares +libuuid +libupnp +libpjnath +libmxml +sqlite +NatClient
  DEPENDS  += +sysevent +ulog +subdevice +zigbee_ap
  DEPENDS  += +gnupg
endef

define Package/WeMo_Link/description
	WeMo Link primary application
endef

define Build/Prepare
endef

define Build/Compile
endef

define Package/WeMo_Link/install
	$(CP) ./files/* $(1)/
	rm -rf $(1)/usr/include
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/include $(1)/lib
	$(CP) ./files/usr/include/* $(1)/include
	$(CP) ./files/lib/* $(1)/lib
endef

$(eval $(call BuildPackage,WeMo_Link))

