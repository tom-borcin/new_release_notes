_This example shows **NEW** Release notes Changelog for **Core System** functional area/team. Release notes Changelog would be stored in Changelg document under **docs** folder in ESP-IDF repository.
Full Changelog path for this case: `espressif/esp-idf/docs/changelog/pre-release-v4.4-beta1.md`_

_Major changes are presented in Release notes under `releases` page on Github while Changelog file contains all remaining changes._

_New sections are added into Changelog document:_
- _Added: section lists added features/functionalities_
- _Changed: section lists changed features/functionalities_
- _Deprecated: section lists newly deprecated features/functionalities_
- _Fixed: section lists bugfixes_
- _Removed: section lists removed features/functionalities_

_Changes are evaluated from customer perspective. For example `Remove duplicate warning` change wont fall into Removed section, because from Customers' perspective it doesn't remove feature/funtionality.
`Remove duplicate warning` belongs into Fixed section because duplicate warning is bug and this change fixes it._




====================Changelog Example====================

## IEEE 802.15.4

**Added**
* Added IEEE 802.15.4 component, support IEEE 802.15.4 driver with pre-build library
* Added Zigbee pending mode and config coordinator API

**Changed**
* Set IEEE 802.15.4 default PTI to 6

## OpenThread

HIGHLIGHT_EXAMPLE:
_Bad entry, mixes additions and removals. Must be split into two: one for addition and one for removal_
* Remove openthread-core-esp32x-config.h, added openthread-core-esp32x-cli-config.h and openthread-core-esp32x-rcp-config.h

**Added**
* Added OpenThread submodule
* Added OpenThread porting for ESP32
* Added OpenThread cli example
* Added otPlatRadioSetMacKey and otPlatRadioSetMacFrameCounter implementation.
* Support microsecond timer
* Added esp_openthread_netif_init() api for initializing the OpenThread lwIP interface.
* Added OpenThread lwIP interface to the ot_cli example.
* Enable ot_cli on ESP32H2-Beta chip
* Enable multicast ping in OpenThread examples by default
* Added esp_cli_custom_command
* Added TCP/UDP socket example
* Added esp_openthread_init esp_openthread_launch_mainloop and esp_openthread_deinit for simplified OpenThread initialization and launch logic.
* Added the OPENTHREAD_BORDER_ROUTER Kconfig option
* Added platform UDP and task queue port for the border agent feature
* Added esp_openthread_border_router_* api
* Added the esp_otbr example.
* Introduced a config option to enable/disable extended features in ot_cli example
* Support ICMPv6 auto config
* Support SRP service delegation
* Added ftd.cmake for build FTD and radio.cmake for build RCP
* Openthread enable ping sender module
* Support discovery delegate in border router
* Added iperf example
* iperf: Support IPV6 address
* iperf: Added new field len_send_buf, now iperf can set the length of sending buffer
* OpenThread: Added menuconfig option to enable srp client
* Enable dynamic logging
* Added esp_openthread_cli APIs
* Added history support for OpenThread CLI

**Changed**
* Updated the OpenThread cli example with the simplified implementation.
* Porting and border routing features are now provided by prebuilt libraries
* esp_openthread_netif_glue_init now requires platform config as its parameter
* Publish _meshcop._mdns service
* iperf: Merge socket send/recv logic
* Reduce default log verbosity

**Fixed**
* Updated OpenThread submodule to contain TCP message leak fix.
* Fixed wrong uart read return value handling

## Bluetooth Controller

**Added**
* Added high level interrupt for Bluetooth
* Support ESP32-S3-Beta3 BLE

**Changed**
* Disabling asserts for the entire project (or setting silent) now applies to BT assert configurations
* Created repository for BLE library files of ESP32-C3 and ESP32-S3, as a new submodule of ESP-IDF. Modify directory layout to better support multiple chips.

**Fixed**
* Fixed bluetooth controller task watchdog in Wi-Fi test
* Fixed live lock issue in Bluetooth interrupt immediately, to make sure interrupt response speed
* Fixed the assert in checking hardware sleep state during wake-up
* Fixed rx interrupt flooding during BLE scan event in coexistence scenario, in the case that no Rx buffer is available.
* Use correct addresses of Bluetooth Low Power Clock registers on Chip 7.2.8 ESP32-S3
* Fix for C2H flow control parameter check in Bluetooth controller. Required for Nimble Host flow control to work
* Fixed interrupt watchdog timeout during controller disable procedure for ESP32-S3/ESP32-C3
* Fixed the Rx performance issue for coded PHY, especially in coexistence scenario for ESP32-C3/ESP32-S3
* Fixed: Power down bluetooth module when deinit
* Fixed the issue caused by the power off the BT/Wi-Fi power domain

**Removed**
* Delete the option: BLE ADV priority high

### Bluetooth Low Energy

**Added**
* Supported HW CCA

**Fixed**
* Fixed the bug of modem sleep which may lead to the crash issue "assert(-218959118,0)" 
* Fixed controller do not report disconnect event to host
* Fixed BLE disconnect due to connection parameters update
* Fixed the start scan crash issue
* Removed duplicate events in r_lld_evt_end
* Fixed update exception list assert
* Fixed no adv report in scan when using HW reconnect
* Fixed data length update rejected when controller is updating data length
* Fixed BLE ACL Tx Flush issue during Reset/Reboot
* Fixed the scan timeout report
* Fixed that when EXT CRYS is configured but not detected, light sleep is still allowed to be used.
* Fixed controller default LE Event Mask, the origin value is {0xFF,0xFF,0x0F,0x00,0x00,0x00,0x00,0x00}, the current value is {0x1F,0x00,0x00,0x00,0x00,0x00,0x00,0x00}.
* Fixed disconnection due to MIC failure (error code:0x3D) during pairing is fixed
* Fixed BLE controller init failed due to version number mismatch for ESP32-S3
* Fixed missing the sleep time
* Fixed crash when shutdown bluetooth


### Classic Bluetooth

**Changed**
* Modify E8192 ELx200 ELx40 log level to LOGD.
* Decouple Wi-Fi and bluetooth with coexist to reduce binary file size

**Fixed**
* Fixed IRAM_ATTR missing in coex mode
* Fixed crash in Bluetooth when esp_restart
* Fixed some issues during light sleep and DFS
* Fixed issue that function called in ISR is not labeled with "IRAM_ATTR" in Bluetooth Controller in ESP32-S3
* Fixed wrong Tx Power level mapping and implemented Tx power set/get APIs
* Fixed handling of invalid feature page response.
* Fixed crash when lmp flooding
* Fix unable to initiate SCO connection when peer device not accept sniff mode
* Fix Link error of Bluetooth Kconfig
* Fixed the scan failed issue
* Fixed connection failed with LG 5.0 phone
* Fixed crash after inquiry has finished
* Fixed crash caused by bluetooth high level interrupt

## Bluedroid

### Classic Bluetooth

**Added**
* SPP：Added API esp_spp_stop_srv_scn to stop a specific server
* SPP：Added parameter service_name with event ESP_SPP_DISCOVERY_COMP_EVT
* SPP：Added parameter scn with event ESP_SPP_START_EVT
* SPP：Added parameter scn with event ESP_SPP_SRV_STOP_EVT
* SPP: Added some common FAQs in SPP Demo README.
* HID: Added configuration of HID task stack size (https://github.com/espressif/esp-idf/pull/6385)
* HID: Added BTC layer and API for HID host
* HID: Support HID Device role over BR/EDR

**Changed**
* Shortened some log messages in bluedroid

**Fixed**
* SPP: Fixed a crash caused by pairing cancel
* HFP: Fixed crash in btc_hf_arg_deep_copy when name or number is NULL.
* Fixed L2CAP Repeat CID
* HFP: Fixed build error for HFP-HF when bluedroid dynamic memory allocation is enabled.
* HF-AG: Fix ag use dynamic memory error.
* Fixed C3/S3 multi-connection failed when device acts as master and slave at the same time
* A2DP: Fixed A2DP sink blocked issues.
* SPP: Fixed SPP acceptor deadlock
* A2DP: Fixed A2DP deint crash
* SPP: Fixed SPP memory leak
* Fixed the timer collision in function bta_sys_start_timer() used by role switch.
* HFP: Fixed issue that acl can't disconnect when hfp_client disconnect.
* Fixed the crash when using legacy paring with wrong pin code
* Fixed wrong clock_id in function time_now_us
* Fixed single-tone sample sequence generation error in HFP examples
  

### Bluetooth Low Energy

**Added**
* Added option to enable/disable ESP32 controller RPA 
* Added an option in menuconfig to configure maximum GATT services 
* Added reconnection function to try reconnect after the connection fails to be established 
* Added option to enable multi-connection 
* Supported HID examples for ESP32-C3 and ESP32-S3 
* Added UHCI example to ESP32-C3, used for Bluetooth Controller only mode through HCI UART transport
* Added check if the BLE extend connection parameter is valid

**Changed**
* Optimize multi-connection for ESP32-C3 and ESP32-S3 
* Updated connection state when getting connection cancel complete
* Modify ambiguous descriptions for BT_CTRL_BLE_MAX_ACT
* Modify parameter description for esp_ble_gattc_open()

**Fixed**
* Fixed bluedroid host report connection address error when remote device used RPA address 
* Fixed multi-connection pair failed 
* Fixed iPhone repaired failed for ESP32-C3 and ESP32-S3 
* Fixed BLE 5.0 pairing failed when using random address 
* Fixed reconnect failed when using rpa public address 
* Fixed BLE ANON_ADV address error 
* Fixed crash due to enable GATTC NVS cache 
* Fixed issue of option not being set due to incorrect macro name 
* Fixed BLE can't resolve the peer address when whitelist is enabled for ESP32. 
* Fixed BLE connection will crash during erase flash 
* Fixed data length update failed
* Fixed Spelling mistakes
* Fixed Bluedroid Host auto update PPCP after exchange connection parameters

## NimBLE

**Changed**
* Updated custom logging support for NimBLE host.
HIGHLIGHT_EXAMPLE:
_Could be change or fix, depends on result_
* Check stack initialization status before executing stack commands 

**Fixed**
* Fixed WDT crash observed during security exchanges.
* Fixed max connection configuration issue in ESP32-C3.
* Fixed ‘Impersonation in the Passkey Entry Protocol’ Vulnerability. 
* Fix issue of crash during timer deletion

* Added separate option to enable bonding which fixed forget device iOS issue
* Blufi on Nimble: Added fix for crash issue on ESP32-C3 during application init.

**Removed**
* Removed critical log level value from menuconfig.


## ESP-BLE-Mesh

**Added**
* Added check of Provisioning Random & Confirmation sent/received by Provisioner (CVE-2020-26556 & CVE-2020-26560). 

**Changed**
* Recommend to use OOB mechanism to exchange Public Key (CVE-2020-26559)
* Recommend to use randomly generated AuthValue for Static OOB (CVE-2020-26557) 
* Make Unprovisioned Device Beacon interval configurable
* Update the SIG recommendations for BLE Mesh CVE issues 
* Apply the errata E16350 of BLE Mesh from Bluetooth SIG

**Fixed**
* Fixed using wrong endianness of input/output authentication number for Provisioner 
* Fixed provisioning input/output authentication number should be at least 1 
* Fixed filtering error when Provisioner receives heartbeat messages


## Wi-Fi & BT Coexistence

**Added**
* Support external coexistence when WiFi starts, customers can use it for extending the other communication protocols to the mechanism of time diversion.

**Fixed**
* Coexistence: Fixed performance issue for extended active scan in coexistence scenario: use the same priority for Rx of AUX_ADV_IND and AUX_SCAN_RSP <sup>(1)</sup>

## Wi-Fi Mesh

**Added**
* Added support for chain topology <sup>(1)</sup>
* mesh/ps: Added esp_mesh_ps_duty_signaling to accelerate the broadcast of new network duty. <sup>(1)</sup>
* mesh/recv: Added option MESH_OPT_RECV_RATE (esp32-only). <sup>(1)</sup>
* mesh: Added esp_mesh_send_block_time to set blocking time of esp_mesh_send <sup>(1)</sup>
* Added non mesh connections access <sup>(1)</sup>

**Changed**
* mesh/rssi: Average the router_rssi. <sup>(1)</sup>
* mesh/ps: Close NWK-DUTY-MASTER process.<sup>(1)</sup>
* mesh/root: Change the condition of s_extra_scan_attempts <sup>(1)</sup>
* mesh/ps: Modify beacon interval to 300ms when ps is enabled. <sup>(1)</sup>
* esp_mesh_send is blocked in nodes(layer>=3), when a FIXED-ROOT root is duty master <sup>(1)</sup>

**Fixed**
* mesh/c3: Fixed mesh deinit blocking issue <sup>(1)</sup>
* mesh/c3: Fixed root has no eb for deauth frames during the networking <sup>(1)</sup>

**Removed**
* mesh/ps: Remove ps duty info from the ADD announcement packets.<sup>(1)</sup>
* mesh/ps: Remove the support of MESH_PS_NETWORK_DUTY_APPLIED_UPLINK. <sup>(1)</sup>


## Wi-Fi

**Added**
* Support disabling 11b rate <sup>(1)</sup>
* Support configuring ESP-NOW rate <sup>(1)</sup>
* Added encrypt option for ESPTouch v1 <sup>(1)</sup>
* Support to sleep for station in disconnected status.<sup>(1)</sup>
* Support to adjust wake-up ratio for ESP-NOW at disconnected status. <sup>(1)</sup>
* Added beacon timeout event. <sup>(1)</sup>
* Support phy calibration data save to nvs for ESP32-S2, ESP32-C3 & ESP32-S3  <sup>(1)</sup>
* Added ASAP mode support in FTM operations. In FTM Responder mode, added support for up to 3 FTM initiators simultaneously  <sup>(1)</sup>
* Added support of regdomain database.<sup>(1)</sup>
* Added SHA384/SHA512 support for internal client. <sup>(1)</sup>
* Support embedding multiple phy init data bin into app bin. <sup>(1)</sup>
* Support ESP32-S3 Beta3 Wi-Fi.
* Added sniffer example FCSFAIL filter
* Added a new API to destroy default WiFi network interface created with esp_netif_create_default_wifi_...() API.
* Added station based check for auth frame formation
* PHY: Added esp_phy component and esp-phy-lib submodule
* Support configuring 802.11 tx rate
* Added support of wifi power save for ESP32-S3
* Added support for MBO certification
* Added GCMP, GCMP256, GMAC, GMAC256 support for ESP32C3/ESP32S3.
* Added WPA3 192bit certification support.

**Changed**
* Modify not to store the default value in NVS<sup>(1)</sup>
* Keep wakeup state during csa <sup>(1)</sup>
* Updated libphy.a to V1800 20210413_e7ef680 for ESP32-S2 <sup>(1)</sup>
* Disable FTM by default for non-FTM examples to save space <sup>(1)</sup>
* Update ESP32-C3 phy init data <sup>(1)</sup>
* Cleaned GTK after disconnect <sup>(1)</sup>
* Updated ESP32-C3 Wi-Fi iperf default config. <sup>(1)</sup>
* Validate FTM Initiator config parameters and propagate status <sup>(1)</sup>
* Compile WiFi library with -Os instead of -Og <sup>(1)</sup>
* Added WPS strict config option <sup>(1)</sup>
* Optimize Wi-Fi DTIM sleep current
* Modified connect example to add scan mode config
* Restructured wpa_supplicant's crypto code.
* Refactor WiFi ioctl function <sup>(1)</sup>
* Updated WiFi Enterprise example.

**Fixed**
* Fixed the issue that connect scan may cause crash <sup>(1)</sup>
* Fixed potential crash or watchdog during FTM <sup>(1)</sup>
* Fixed return type of esp_wifi_deinit when Wi-Fi is not stopped <sup>(1)</sup>
* Fixed an issue that Wi-Fi stack may crash when receive AMSDU length bigger then 3200 <sup>(1)</sup>
* Fixed miss-overwrite of some PHY registers when Wi-Fi modem sleep is enabled. <sup>(1)</sup>
* Fixed issue of reason code change from 15 to 200 when provided with wrong password <sup>(1)</sup>
* Fixed the issue that the parameters obtained from RAM cannot be saved to NVS <sup>(1)</sup>
* Fixed issue with hidden AP scans after connecting to an AP <sup>(1)</sup>
* Fixed watchdog issue when receiving action frame <sup>(1)</sup>
* Fixed issue of reason code change from 15 to 204 when provided with wrong password <sup>(1)</sup>
* Fixed set_config return value error <sup>(1)</sup>
* Fixed ampdu age timer memory leak <sup>(1)</sup>
* Fixed the second distribution network failure of ESPTouch v2 <sup>(1)</sup>
* Fixed ESPTouch v2 issues <sup>(1)</sup>
* Update TBTT when rx probe response after beacon timeout <sup>(1)</sup>
* Current stays low at light sleep when using gpio to wake up. <sup>(1)</sup>
* Prevent reinstallation of an already in-use group key <sup>(1)</sup>
* Fixed error in setting channel after WiFi stop <sup>(1)</sup>
* Fixed Block Ack setup issue in PMF scenario <sup>(1)</sup>
* Fixed crash when csi is enabled<sup>(1)</sup>
* Fixed pm state error when csi cb function called <sup>(1)</sup>
* Fixed amsdu and fragment vulnerabilities. <sup>(1)</sup>
* Fixed aes_unwrap functionality  <sup>(1)</sup>
HIGLIGHT_EXAMPLE:
_Bugfix, not change_
  * Move unused wifi log to noload section to save binary size <sup>(1)</sup>
* Fixed RM capability missing for open mode AP<sup>(1)</sup>
* Fixed memory leak under 11KV macro <sup>(1)</sup>
* Fixed connection failure caused by sleep <sup>(1)</sup>
* Fixed nvs init status issue. <sup>(1)</sup>
* Fixed memory leak in esp_issue_scan error path <sup>(1)</sup>
* Clear WLAN_FC_STYPE_ACTION bit in esp_register_action_frame <sup>(1)</sup>
* esp_supplicant: Make esp_rrm_send_neighbor_rep_request return proper error <sup>(1)</sup>
* wpa_supplicant: Trivial typo fix for setting spp_sup.require <sup>(1)</sup>
* Fixed PMF issue with broadcast deauths with certain reason codes <sup>(1)</sup>
* Fixed FTM not working in connected state issue <sup>(1)</sup>
* Fixed airkiss and esptouch find channel crash issue<sup>(1)</sup>
* Fixed enterprise connection issue with windows radius server <sup>(1)</sup>
* Fixed interoperability issue with Windows 2008 radius server. <sup>(1)</sup>
* PHY: Init phy data to default if invalid in flash partition to avoid bootloops
* Fixed WiFi data rate status bug after disconnection.
* Fixed WiFi tx bug in low data rate.
* WPA_Supplicant] Fix supplicant debug logs errors.
* Fixed WAPI Key mgmt compatible issue
* Fixed 9Mbps data rate Tx issue
* Fixed 80211 tx crash issue
* Fix ESP32-S3 malloc rom funcs ptr in psram when psram enable.
HIGHLIGHT_EXAMPLE:
_Bugfix, not added feature_
  * Added missing cflag CONFIG_SHA256 for Makefile  
* wpa_supplicant: Fix wps_free_pins to remove all pins
* Fixed wifi and bt power domain leakage current in light sleep
* Fixed Test PHY/RTC functions called when cache is disabled of ESP32
* Fixed ESP32-C3/ESP32-S3 PHY cause USB no log issue
* Fixed ESP32-C3/ESP32-S3 RSSI change with bandwidth issue

## Core System

**Added**
* VDD_SDIO power domain can now be configured to remain on during light sleep. <sup>(1)</sup>
* SOC: Added dummy bytes to end of flash.text to prevent errors with CPU prefetching instructions past the end <sup>(1)</sup>
* Added option to enable Undefined Behavior Sanitizer (UBSAN)  
* Make longjump context switch-save <sup>(1)</sup>
* esp-timer: Helper function to identify the status of timer <sup>(1)</sup>
* Enable cache access error interrupt on ESP32-S3 
* esp_system: Added sync of FRC & RTC counters in esp_restart <sup>(1)</sup>
* Support .bss segment placed in spiram for ESP32-S2 
* Support NOINIT segment on SPIRAM (https://github.com/espressif/esp-idf/pull/4728) 
* CXX: Added virtual destructor in I2C class <sup>(1)</sup>
* Added ESP32-S3 Beta 3 chip support (replaces ESP32-S3 Beta 2)
* Added Kconfig option to disable boot ROM log
* esp_timer: Added a Kconfig option to set the interrupt level for esp_timer ISR
* esp_timer: Added ESP_TIMER_ISR dispatch method
* Possible to build the firmware with no embedded file paths in the binary (https://github.com/espressif/esp-idf/issues/6306)
* Added config item to select core affinity for main task under SMP (https://github.com/espressif/esp-idf/pull/6627)
* esp_common: Added generic check macros
* Added option to set maximum compile time log level higher than default (https://github.com/espressif/esp-idf/issues/5542)
* Added new startup_time example
* Pthread condition variable static initializer PTHREAD_COND_INITIALIZER is now supported
* Added missing 64-bit stdatomic operations (https://github.com/espressif/esp-idf/issues/3163)
* Added support for specify the maximum descriptor length when setting up the DMA descriptor link
* log: Added Linux implementation of normal log functions
* Added support describe structures of efuses in efuse_table
* SOC: Updated to support ESP32-S3 chip (copy from ESP32-S2)
* Added esp_log_level_get() function (https://github.com/espressif/esp-idf/pull/6573/)
* efuse: Burn operation does not block reading
* esp_timer: esp_timer_get_next_alarm() will not return time for timers with skip_unhandled_events
* Added new CMake function to help mocking whole components
* RISCV-ULP: Added delay utility functions
* RISCV-ULP: Added DS18B20 1wire example
* esp_system: support backtrace on panic for RISC-V boards. 
* Memory layout is now part of heap component
* CXX: Added VA_OPT(,) support for C++20
* Updated esp_efuse_table.csv, added extended 2 bytes mac address and BOOT_DISABLE_FAST_WAKE for ESP32-H2.
* Added new choice of target ESP32-H2 in efuse_table_gen.py
* efuse: Added support custom MAC address stored in the eFuse for ESP32-C3, ESP32-S2, and ESP32-S3
* esp_rom: added implementation for linux 
* esp_ipc: Added API for IPC to run small pieces of code on the other CPU
* Added support of auto light sleep for ESP32-S3
* esp_timer: added mocking of esp_timer
* ROM: Added common API for tjpgd library in the esp_rom
* Cache: Support 16KB DCache size for ESP32-S3
* Cache: Register flash2spiram info to ROM for ESP32-S3
* XTWDT: Added basic support for xtal32k watchdog timer for ESP32-S2/ESP32-S3/ESP32-C3
* Pthread: reader-writer locks implementation
* SoC: Added reset reason header into soc component
* usb_serial_jtag: Support using usb-serial-jtag as default console

**Changed**
* Improve chip boot time for ESP32-S2 <sup>(1)</sup>
* Place xtensa_intr_asm into IRAM <sup>(1)</sup>
* Reset Core0 after disable cache in esp_restart_noos() <sup>(1)</sup>
* digital & rtc dbias of different chip may set to a different value according to pvt scan by ate; <sup>(1)</sup>
* digital & rtc voltage mostly higher than before when cpu run 40M. <sup>(1)</sup>
* Move ETS_T1_WDT_INUM, ETS_CACHEERR_INUM and ETS_DPORT_INUM to l5 interrupt <sup>(1)</sup>
* ULP: Updated CONFIG_ULP_COPROC_RESERVE_MEM max value to reflect the max available memory <sup>(1)</sup>
* ULP: updated the ld file for riscv ulp for ESP32-S2
* Calling esp_log_level_set("*", level) now also changes the log output of ESP_DRAM_LOG and ESP_EARLY_LOG macros (https://github.com/espressif/esp-idf/issues/2285)
* Xtensa: Changed the way assembly files jumps to functions located in another compilation unit
* SOC: Moved peripheral linker scripts to soc component

**Deprecated**
* ESP32-S3 Beta 3 support deprecated, replaced by ESP32-S3 support

**Fixed**
* Fixed delay between interrupt request and interrupt trigger <sup>(1)</sup>
* ULP: Fixed build system bug where linker script wasn't updated if memory reserved for ULP changed. <sup>(1)</sup>
* ULP: Fixed build system bug where linker script wasn't updated if memory reserved for ULP changed. <sup>(1)</sup>
* Fixed possible deadlock when using pthread_join() and log level set to Debug or higher <sup>(1)</sup>
* Fixed potential failure to start in ESP32-S2 RISC-V ULP <sup>(1)</sup>
* Fixed the internal devices/registers access corruption due to concurrent read/write by a spinlock. <sup>(1)</sup>
* Pthread thread-local destructor functions are now called with the ordering required by the specification (https://github.com/espressif/esp-idf/issues/6643) <sup>(1)</sup>
* CXX: Fixed I2C master timeout 
* esp_event: Fixed and improved docs 
* Fixed regression of cache access error not getting detected for APP CPU core on ESP32 
* efuse: Fixed len of SOFT_DIS_JTAG eFuse from 2 to 3 for ESP32-C3 and ESP32-H2 <sup>(1)</sup>
* Fixed the sizes of .text and .rodata segments on ESP32-S2 <sup>(1)</sup>
* partition_table: Fixed case when a few similar to otadata partitions are in the table <sup>(1)</sup>
* Fixed auto adjust voltage bug on ESP32-C3  <sup>(1)</sup>
* rtc clock calibration: Fixed multi-calibration process protection logic  <sup>(1)</sup>
* Bootloader: Fixed bootloader considering a load end address invalid if it was at the end of a memory area <sup>(1)</sup>
* Fixed possible issues with duplicate definitions of likely/unlikely macros (https://github.com/espressif/esp-idf/issues/6445)
* Fixed large number of "unused variable" warnings when asserts are disabled
* Fixed rtc watchdog reset when running multicore app on single core variant of target; abort instead
* hHAL: re-structured duplicated HAL layer functions
* Fixed a bug preventing user from putting panic handlers outside of the IRAM.
* CXX: Fixed C++ exception stubs. No linkage of large unwinding code parts when building with -fno-exception anymore.
* spi_flash/encrypt: Fixed esp_flash_encrypted write (https://github.com/espressif/esp-idf/issues/6254) (https://github.com/espressif/esp-idf/issues/6322)
* Fixed compilation of esp32/spiram.h from C++ code (https://github.com/espressif/esp-idf/pull/6658)
* log: excluding log_linux.c correctly now
* Fixed bug where pthread_cond_timedwait() could return a timeout before abstime timestamp (https://github.com/espressif/esp-idf/issues/6901)
* esp_system: Fixed wrong exception emergency pool allocation
* heap: fix ESP32-C3 build issue with heap tracing enabled
* Fixed redundant target include directories for ESP32 and ESP32-S2
* Fixed the clock gating signal invalid of App cpu core in esp32s3 single-core mode
* Console: Typo fix in cmd_nvs.c
* Fix pm lock bug in dual core mode
* Fixed compiler warning with silent panic option
* Watchdog Timers: Fixed literal overflow issue when calculating Task WDT timeout (https://github.com/espressif/esp-idf/issues/6648)
* CXX: Fixes build error when including gpio_ll.h from cpp file

**Removed**
* Disable ESP32-S2 option "Allow .bss segment placed in external memory", this option is currently only supported on ESP32 <sup>(1)</sup>
* Remove core1 disable cache in cache_utils.c <sup>(1)</sup>
* Update the esp_efuse_table.csv, remove AUTO CONFIG DIG&RTC DBIAS


# Backports

**Added**
* Backport addition 1
* Backport addition 2
* Backport addition 3
* Backport addition 4

**Changed**
* Backport change 1
* Backport change 2
* Backport change 3
* Backport change 4

**Deprecated**
* Backport deprecation 1
* Backport deprecation 2
* Backport deprecation 3
* Backport deprecation 4

**Fixed**
* Backport fix 1
* Backport fix 2
* Backport fix 3
* Backport fix 4

**Removed**
* Backport removal 1
* Backport removal 2
* Backport removal 3
* Backport removal 4