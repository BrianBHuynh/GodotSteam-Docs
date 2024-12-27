---
title: GDNative Changelog
description: A history of all changes made to the gdnative branch.
icon: material/power-plug-outline
---

A history of all changes to [the ***gdnative*** branch;](https://github.com/GodotSteam/GodotSteam/tree/gdnative){ target="\_blank" } which is now retired. This branch still works fine but will not receive any further updates.

---

## Version 3.26

- Added: missing `user_achievement_icon_fetched` callback
- Added: new functions to Apps class
- Added: new Steam Timeline class functions
- Added: new functions to UGC class
- Changed: updated for Steamworks SDK 1.60
- Changed: `network_messages_session_failed` callback now returns the Steam ID associated with the user whose session failed
- Changed: `global_stats_received` had call result name change under-the-hood, does not affect anything
- Changed: `sendMessages()` now returns the message result
- Changed: `getQueryUGCResult()` now passes back additional value total_files_size
- Changed: `item_installed` signal now returns additional data - legacy_content and manifest_id
- Fixed: incorrect signal name for `inventory_definition_update`, ***thanks to Foxushka***

## Version 3.25

- Added: Steam Matchmaking response handlers, ***thanks to jeremybeier***
- Added: all missing Messages and Sockets constants
- Changed: Networking Messages, Sockets, and Utils now use Steam IDs instead of identity system
- Changed: cleaned up `addItemPreviewFile()`, `check_file_signature`, and `showGamepadTextInput()`
- Changed: various bits and pieces
- Changed: IP logic for all related functions
- Changed: `addFavoriteGame()`, `initiateGameConnection()`, `terminateGameConnection()`, and `removeFavoriteGame()` now take strings for IP
- Changed: `getAuthSessionTicket()` now defaults to 0 for Steam ID
- Changed: IP address now accepted instead of IP references
- Fixed: `getFriendCount()` has correct bit-wise value
- Fixed: server browser functionality, ***thanks to jeremybeier***
- Fixed: wrong string IP conversions, ***thanks to jeremybeier***
- Fixed: server list request filters, ***thanks to jeremybeier***
- Fixed: `playerDetails()`, `requestFavoritesServerList()`, `requestInternetServerList()`, `requestSpectatorServerList()`, `requestFriendsServerList()`, `requestHistoryServerList()`, and `pingServer()`, ***thanks to jeremybeier***
- Fixed: regressions caused by minor update
- Removed: Networking Types identity system and related bits
- Removed: P2P Networking constants as they are duplicates of the P2PSend enum
- Removed: previous, non-functioning Matchmaking Server call results
- Removed: `getIdentity()` as it is redundant now

## Version 3.24

- Changed: `createBrowser` now accepts empty strings like the godot3 branch
- Changed: minor organizational things, variable naming, etc.
- Changed: `getItemPrice()` now returns base price and price, ***thanks to SlejmUr***
- Fixed: missing info_flags key in `getSessionConnectionInfo()`, ***thanks to SlejmUr***
- Fixed: `requestClanOfficerList()` using wrong SDK call
- Fixed: issues with `getResultItems()`
- Fixed: `addRequestLobbyListDistanceFilter()`
- Fixed: `getServerDetails()` not sending back needed struct, ***thanks to SlejmUr***
- Fixed: regressions in `receiveMessagesOnChannel()`, `receiveMessagesOnConnection()`, and `receiveMessagesOnPollGroup()`
- Fixed: `getConnectionRealTimeStatus()` checking the wrong value, ***thanks to tamper2***
- Fixed: missing cast on `setSize()`
- Fixed: `addRequiredTagGroup()` backported from godot3 branch
- Removed: unused internal variables

## Version 3.23.1

- Added: internal notes about where enums are found
- Added: minor extra helper functions from Steam's client header
- Added: `getSteamID32()` function to convert SteamID64 to SteamID
- Changed: replaced deprecated Controller struct with Inputs struct in `getDigitalActionData()`
- Changed: in-editor docs
- Changed: leaderboard details max now set at highest instead of zero by default
- Fixed: incorrect constant for PUBLISHED_FILE_UPDATE_HANDLE_INVALID
- Fixed: `getAllLobbyData()` sending back all pairs, ***thanks to freehuntx***

## Version 3.23

- Added: two new Friends class constants
- Added: new function `dismissGamepadTextInput()`
- Added: new general constant ACCOUNT_ID_INVALID
- Removed: App Lists class functions, callbacks, etc. due to SDK 1.59 changes

## Version 3.22.4

- Added: missing k_nSteamNetworkingSend_AutoRestartBrokenSession to constants
- Added: two missing Input constants: INPUT_HANDLE_ALL_CONTROLLERS and INPUT_MAX_ACTIVE_LAYERS
- Changed: `getInputTypeForHandle()` now returns int / enum instead of string for device models
- Changed: order of constants to be alphabetic
- Changed: changed returned variable name to `need_to_accept_tos` in `item_updated` callback

## Version 3.22.3
- Changed: moved constants to separate file like in Godot 4.x branches
- Fixed: `requestClanOfficerList()` using wrong internal function, ***thanks to sepTN***

## Version 3.22.2

- Changed: reverted `steamInit()` and `steamInitEx()` as new methods won't work with GDNative
- Removed: all enums as they cannot be used in GDNative

## Version 3.22.1

- Added: two new arguments to `steamInit()` and `steamInitEx()` to set your app ID and run_callbacks interally, ***thanks to GreenFox***
- Fixed: issue with callback that caused compiling failure in Linux

## Version 3.22

- Added: two Music class callbacks
- Changed: `generateItems()`, `exchangeItems()`, `getItemsByID()`, and `startPurchase()` all list-based arguments are now PoolIntArrays
- Changed: `getItemsByID()` now takes one argument, counts the elements in the passed array instead
- Changed: `getItemsWithPrices()` no longer requires any arguments passed to it
- Changed: in-editor docs have been updated
- Fixed: `getResultItems()` now returns all item data
- Fixed: missing DEFVAL for `steamInitEx()`
- Fixed: Joy Con name in `getInputTypeForHandle()`
- Removed: `getNumItemsWithPrices()` as it was unnecessary

## Version 3.21.3

- Fixed: `requestEquippedProfileItems()` was missing method bind, ***thanks to BOTLANNER***
- Fixed: `get_ticket_for_web_api` callback for getting actual ticket buffer, ***thanks to dicarne***
- Fixed: compiler complaining about comparison between Steam enum and GodotSteam enum for `steamInitEx()`
- Fixed: `getListenSocketAddress()` fixed to provide the actual address and optional port
- Changed: `createBrowser()` now sends proper NULL when empty string passed
- Changed: `html_browser_ready` from callback to proper call result
- Changed: cast handle in `setSize()` as Steam HHTMLBrowser
- Removed: unnecessary steam_appid.txt from zips in Github Actions

## Version 3.21.2

- Fixed: missing descriptions for some in-editor functions/signals
- Fixed: `receiveMessagesOnChannel()`, `receiveMessagesOnPollGroup()`, and `receiveMessagesOnConnection()` had overwriting dictionary keys

## Version 3.21

- Added: new enums and constant related to new Steam initialization function
- Added: new enums for NetworkingConfigValue
- Added: new intialization function `steamInitEx()` that is more verbose
- Added: new UGC function `getUserContentDescriptorPreferences(0`
- Added: new Remote Play function `startRemotePlayTogether()`
- Changed: UGC function`setItemTags()` to have new argument for admin tags
- Changed: compatible with Steamworks SDK 1.58

## Version 3.20.1

- Fixed: wrong variant type for `join_requested`

## Version 3.20

- Added: `steamShutdown()` to allow Steamworks to be manually shutdown
- Added: `requestEquippedProfileItems()` function and `equipped_profile_items` callback
- Added: Steam Deck as Steam Input type
- Changed: all enums are now directly linked to their SDK counterparts
- Changed: `getDigitalActionData()` returned keys are now state and active
- Changed: names of some Steam enums to be cleaner and leaner
- Changed: `getAppInstallDir()` now returns dictionary with absolute path and install size
- Fixed: missing function argument binds
- Removed: enums that are not in the SDK but Valve's docs

## Version 3.6.2

- Added: new Input callback `input_gamepad_slot_change`
- Added: new User callback `get_ticket_for_web_api`
- Added: new User function `getAuthTicketForWebApi()`
- Fixed: `lobby_match_list` callback, but no sends the lobby count along with the lobby list array (only in GDNative due to weird GDNative bug)
- Changed: `getAuthSessionTicket()` argument is now optional, defaults to NULL

## Version 3.6.1

- Added: new return values for `overlay_toggled`; this will break compatibility with this
- Added: new UGC functions `removeContentDescriptor()`, `addContentDescriptor()`, and `getQueryUGCContentDescriptors()`
- Added: new signal `filter_text_dictionary_changed`
- Changed: `getAuthSessionTicket()` now uses networking identities
- Changed: `gamepad_text_input_dismissed` now passes back the app ID
- Changed: Steam Input max analog and digital actions values
- Fixed: `lobby_match_list` callback, but it now passes back the lobby count too
- Removed: ERegisterActivationCodeResult due to removal in SDK

## Version 3.6

* Changed: brought the plug-in version up to speed with the module version

## Version 3.5.1

* Changed: `createSteamID()` function to use proper 64-bit int
* Changed: brought the plug-in version up to speed with the module version
* Changed: output from `subscribe_item`, `unsubscribe_item` file_id to uint64_t
* Fixed: some new compiling quirks
* Removed: `setIdentitySteamID()` and `getIdentitySteamID()`

## Version 3.5

* Fixed: incorrect type for `getAppListBuildId()`

## Version 3.4.1

* Fixed: OSX naming of DyLib files

## Version 3.4

* Added: `setDLCContext()`, `getProfileItemPropertyString()`, `getProfileItemPropertyInt()`, `hasEquippedProfileItem()`, `getPublicIP()`, `getPSNID()`, `getStadiaID()`, `getXboxPairwiseID()` functions
* Added: handle arguments to HTML Surface class functions
* Added: inventory handle arguments to Inventory class functions
* Added: networking identity references into new Networking class functions
* Added: `equipped_profile_items_changed`, `equipped_profile_items` callbacks
* Added: additional data types to signals
* Changed: many functions in Networking Sockets and Networking Types classes
* Changed: newtorking identity maps
* Changed: various argument names to fall in line with module version
* Changed: renamed some signals
* Fixed: `serverInit()`, `advertiseGame()` functions
* Fixed: `getSessionID()` using wrong type in Remote Play class
* Fixed: various incorrect types in Screenshots class
* Fixed: wrong int type for inventory update handle
* Fixed: not casting app ID for `addFavoriteGame()`
* Fixed: wrong int type for server ID in `getLobbyGameServer()`
* Removed: `requestAllProofOfPurchaseKeys()`, `requestAppProofOfPurchaseKey()` functions and related callbacks
* Removed: leading dash from signal / callback function names

## Version 3.3

* Added: missing D_METHOD to all functions, should show the right argument names in-editor
* Added: Input origin enums for PS5 and Steam Deck
* Added: Input Types, Input Glyph Style, Input Glyph Size, and Input Configuration Enable Type enums
* Added: `getConnectionRealTimeStatus()`, `configureConnectionLanes()`, `connectP2PCustomSignaling()`, `receivedP2PCustomSignal()`, `getCertificateRequest()`, `setCertificate()`, `resetIdentity()`, `runNetworkingCallbacks()`, `beginAsyncRequestFakeIP()`, `getFakeIP()`, `createListenScoketP2PFakeIP()`, `getRemoveFakeIPForConnection()`, and `createFakeUDPPort()` functions and callback to NetworkingSockets class
* Added: `dismissFloatingGamepadTextInput()` function to Utils class
* Added: `setTimeCreatedDateRange()` and `setTimeUpdatedDateRange()` to UGC class
* Added: NetworkingeDebugOutputType enums for NetworkingUtils
* Added: missing constant binds for Server API, OverlayToWebPageMode
* Added: server branch merged in
* Fixed: minor compiler warnings
* Fixed: empty file hash being returned by `file_details_result` callback
* Fixed: a variety of small bugs and possible crashes, ***thanks to qarmin***
* Fixed: missing binds for `getFriendsGroupName()`, `getFriendsGroupMembersList()`, `getFriendsGroupIDByIndex()`, `getFriendsGroupCount()`, `getFriendMessage()`, `getFriendCoplayTime()`, `getFriendCoplayGame()`, `getCoplayFriendCount()`, `getCoplayFriend()`, `getClanTag()`, `getClanName()`, `getClanCount()`, `getClanChatMessage()`, `getClanByIndex()`, `getClanActivityCounts()`, `fileWriteAsync()`, `fileWriteStreamCancel()`, `fileWriteStreamClose()`, `fileWriteStreamOpen()`, `fileWriteStreamWriteChunk()`, `getCachedUGCCount()`, `getUGCDownloadProgress()`, `getUGCDetails()`, `fileReadAsync()`, `getOPFSettings()`, `getOPFStringForApp()`, `getVideoURL()`, `isBroadcasting()` functions
* Fixed: `setPNGIcon()` and `updateCurrentEntryCoverArt()` in Music Remote class
* Fixed: missing `getUGCDetails()` and `getUGCDownloadProgress()` functions
* Changed: spacing in default arguments in [godotsteam.h]
* Changed: renamed STEAM_GAMESERVER_CALLBACK as STEAM_CALLBACK
* Changed: updated doc_class file for in-editor documentation
* Changed: updated to Steamworks 1.53
* Changed: `lobby_data_update`, removed lobby data queries as they should be done manually
* Changed: minor tweaks under-the-hood
* Changed: various generic 'int' to their actual types
* Changed: renamed servers and server stats to game server and game server stats respectively, to match SDK
* Changed: SteamNetworkingQuickConnectionStatus to SteamNetConnectionRealTimeStatus_t per Steamworks SDK 1.53, causes a break in previous GodotSteam versions
* Changed: `getConfigValueInfo()`, removed name and next value from return dictionary as they are no longer passed by function in SDK 1.53
* Changed: rearranged functions in godotsteam.cpp class binds to match [godotsteam.h] order
* Changed: enum constant binds to match [godotsteam.h] enum order
* Removed: unused callback `new_launch_query_parameters`, `broadcast_upload_start`, `broadcast_upload_stop`
* Removed: `allocateMessage()` as it shouldn't be used solo
* Removed: `getQuickConnectionStatus()` and `getFirstConfigValue()` as they were removed from SDK 1.53
* Removed: `setDebugOutputFunction()` from Networking Utils
* Removed: unused structs
* Removed: SteamGameServer_RunCallbacks function

## Version 3.2

* Added: new helper functions for newer networking classes, translations for steamnetworkingtypes
* Changed: now works in Godot 3.4
* Fixed: various compiler warnings

## Version 3.1.1

* Removed: not logged in as a failure condition for `steamInit()`

## Version 3.1

* Added: various Steam Deck specific functions, ***thanks to EIREXE***
* Added: new AppLists class of functions and callbacks
* Added: new or missing App functions, callbacks, and enums
* Added: OverlayToWebPageMode enum and `unread_chat_messages_changed` callback for Friends class
* Added: new Input functions and callbacks
* Added: new Parental Settings fuctions, callback, and enums
* Added: new Remote Storage functions, callback, and enums
* Added: new UGC functions, callbacks, and enum
* Added: memory allocation corrections
* Changed: updated various Input class functions
* Changed: lots of argument names internally, has no effect on usage
* Fixed: some enum names
* Fixed: various server list filter functions in Matchmaking Servers class
* Fixed: `getGameCoordinatorServerLogin()` in Networking Sockets class
* Removed: `receiveRelayAuthTicket()`, `findRelayAuthTicketForServer()`, `getHostedDedicatedServerAddress()`, and `getGameCoordinatorServerLogin()` as they rely on datagram header that was removed from base SDK
* Removed: second call for steam_api.h in godotsteam.cpp

## Version 3.0.1

* Fixed: two issues with godotsteam.cpp that causes compiling error on Linux

## Version 3.0.0

* Added: all missing functions to bring GDNative version in-line with module version
* Changed: rebuilt and restructured layout of project folder
* Removed: enums as they don't work in GDNative
* Removed: default arguments for functions as they don't work in GDNative

## Version 2.1.0

* Added: Steamworks P2P functions thanks to Antokolos

## Version 2.0.0

* Added: all current GodotSteam functions and signals
* Added: [godotsteam.h] file
* Changed: compile process; ***thanks to willnationsdev***
* Changed: various parts of the CPP files
* Removed: pre-compiled TSCN and TRES files

## Version 1.1.0

* Added: [godotsteam.h] file
* Added: `getCurrentGameLanguage()`
* Added: Pre-compiled engines and templates for Linux, Mac, and Windows
* Added: change log to documentation
* Changed: various parts of the CPP files
* Changed: minor things in godotsteam.cpp
* Removed: pre-compiled TSCN and TRES files

## Version 1.0.0

* Added: most pre-existing GodotSteam code over
* Added: GodotSteam GDNative documentation
* Changed: SConstruct file from GDNative to support architecture recognition or accept bit arguement in SCONS
* Bugs: Windows does not work for compiling yet, waiting for GDNative update
