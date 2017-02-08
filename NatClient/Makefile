include $(TOPDIR)/rules.mk

PKG_NAME:=NatClient
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define NATCLIENT
$$(OUTPUT): $$(OBJS)
	$$(CC) -o $$@ $$^ $$(LDFLAGS)

clean:
	rm -f $$(OUTPUT) $$(OBJS)
endef

TARGET_CFLAGS +=  -I$(STAGING_DIR)/usr/include/upnp
TARGET_LDFLAGS += -lbelkin_nvram -lbelkin_api
TARGET_LDFLAGS += -lthreadutil -lixml -lmxml
TARGET_LDFLAGS += -lAddlInfra -lssl -lcrypto -lcares -lcurl -lz
TARGET_LDFLAGS += -lpjnath-pc-linux-gnu -lpjlib-util-pc-linux-gnu
TARGET_LDFLAGS += -lpj-pc-linux-gnu -luuid -lpmortem

TARGET_LDFLAGS += -lNetworkControl -lDeviceControl -lRemoteAccess
TARGET_LDFLAGS += -lsysevent -lrt -lulog -lUPnPHndlr -lsubdevice -lupnp -lPluginHndlr
TARGET_LDFLAGS += -lzigbee_api -lWemoDB -lsqlite3 -lpmortem
TARGET_LDFLAGS += -lcurl -lcares -lm

EXTRA_CFLAGS += -D_REENTRANT -DTHREADSAFE=1 -D__RINIT_M
EXTRA_CFLAGS += -DPJ_IS_LITTLE_ENDIAN=1 -DPJ_IS_BIG_ENDIAN=0

define Package/NatClient
  CATEGORY := Belkin
  SUBMENU  := Apps
  SECTION  := utils
  TITLE    := NAT client App
  DEPENDS  += +openssl +curl +libcares +libupnp +libmxml
  DEPENDS  += +libpjnath +libuuid +sqlite
endef

define Package/NatClient/description
	WeMo NAT client application
endef

define Build/Prepare
	#$(INSTALL_DIR) $(PKG_BUILD_DIR)
	#echo "$$$$NATCLIENT" > $(PKG_BUILD_DIR)/Makefile
endef

define Build/Compile
	#$(MAKE_VARS) $(MAKE) -C $(PKG_BUILD_DIR)/$(MAKE_PATH) $(MAKE_FLAGS)
endef

define Package/NatClient/install
	#$(INSTALL_DIR) $(1)/sbin
	#$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(OUTPUT) $(1)/sbin/
endef

$(eval $(call BuildPackage,NatClient))

