

include $(TOPDIR)/rules.mk

PKG_VERSION:=1.0.4
PKG_RELEASE:=20220805

LUCI_TITLE:=LuCI support for wxedge
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+docker +luci-lib-iform

define Package/luci-app-wxedge/conffiles
/etc/config/wxedge
endef

define Package/luci-app-wxedge/prerm
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
    uci -q batch <<-EOF >/dev/null
        set firewall.wxedge.enabled="0"
        commit firewall
EOF
	/etc/init.d/firewall reload
fi
exit 0
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature

