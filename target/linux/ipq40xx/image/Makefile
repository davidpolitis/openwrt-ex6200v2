include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Device/Default
	PROFILES := Default
	KERNEL_DEPENDS = $$(wildcard $(DTS_DIR)/$$(DEVICE_DTS).dts)
	KERNEL_LOADADDR := 0x80208000
	DEVICE_DTS = $$(SOC)-$(lastword $(subst _, ,$(1)))
	DEVICE_DTS_CONFIG := config@1
	IMAGES := sysupgrade.bin
	IMAGE/sysupgrade.bin = sysupgrade-tar | append-metadata
	IMAGE/sysupgrade.bin/squashfs :=
endef

define Device/netgear_ex6200v2
    $(call Device/DniImage)
        DEVICE_DTS_CONFIG := config@4
        NETGEAR_BOARD_ID := EX6200v2
        NETGEAR_HW_ID := 29765265+16+0+256+2x2+2x2
		SOC := qcom-ipq4018
		DEVICE_VENDOR := Netgear
		DEVICE_MODEL := EX6200
		DEVICE_VARIANT := v2
endef
TARGET_DEVICES += netgear_ex6200v2

include $(SUBTARGET).mk

$(eval $(call BuildImage))
