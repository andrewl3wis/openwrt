
# Attribution: https://gist.github.com/lenew/9b41ba901c3393047ede0766760f9d55

#Put this source to 'package/kernel/r8125' folder of OpenWRT/LEDE SDK
#Build(make menuconfig, make defconfig, make)


include $(TOPDIR)/rules.mk

PKG_NAME:=r8125
PKG_RELEASE=9.009.02

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/r8125
  SUBMENU:=Network Devices
  TITLE:=Driver for Realtek 8125 series devices
  DEPENDS:=@PCI_SUPPORT +kmod-mii +kmod-phy-realtek
  FILES:=\
	$(PKG_BUILD_DIR)/r8125.ko
  AUTOLOAD:=$(call AutoProbe,r8125)
  PROVIDES:=kmod-r8125
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,r8125))
