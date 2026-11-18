if(CONFIG_ZMK_DISPLAY AND CONFIG_NICE_VIEW_WIDGET_STATUS AND CONFIG_ZMK_SPLIT
   AND NOT CONFIG_ZMK_SPLIT_ROLE_CENTRAL)
  zephyr_library()
  zephyr_library_sources(corge.c)
  # Redirect both stock art choices while keeping the upstream status widget.
  zephyr_link_libraries(-Wl,--wrap=balloon -Wl,--wrap=mountain)
endif()
