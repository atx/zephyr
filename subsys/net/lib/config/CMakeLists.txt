zephyr_library()
zephyr_library_compile_definitions_ifdef(
  CONFIG_NEWLIB_LIBC __LINUX_ERRNO_EXTENSIONS__
  )

zephyr_library_sources_ifdef(CONFIG_NET_APP_SETTINGS init.c)

if(CONFIG_NET_APP_SETTINGS)
  zephyr_library_sources_ifdef(
    CONFIG_NET_L2_IEEE802154
    ieee802154_settings.c
    )

  zephyr_library_sources_ifdef(
    CONFIG_NET_L2_BT
    bt_settings.c
  )
endif()
