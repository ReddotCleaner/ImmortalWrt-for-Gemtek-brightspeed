# SPDX-License-Identifier: GPL-2.0-only
#
# Airoha SIF-compatible I2C host controller.
#
# Split out of package/kernel/airoha-pon, which was dropped upstream. The
# AN7581 boards (Gemtek XR1710G) keep an NCT7802 fan/thermal controller on
# i2c0, so without this module there is no i2c bus, no hwmon device and no
# way to read board temperature or drive the fan.

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=airoha-i2c
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0-only

include $(INCLUDE_DIR)/package.mk

define KernelPackage/airoha-i2c
  SUBMENU:=Other modules
  TITLE:=Airoha SIF-compatible I2C host controller
  DEPENDS:=+kmod-i2c-core @(TARGET_airoha_an7581||TARGET_airoha_an7583)
  FILES:=$(PKG_BUILD_DIR)/i2c-airoha.ko
  AUTOLOAD:=$(call AutoLoad,12,i2c-airoha)
endef

define KernelPackage/airoha-i2c/description
 Kernel module for the Airoha SIF-compatible I2C host controller used by xPON
 hardware and board sensors (e.g. the NCT7802 fan controller on XR1710G).
endef

$(eval $(call KernelPackage,airoha-i2c))
