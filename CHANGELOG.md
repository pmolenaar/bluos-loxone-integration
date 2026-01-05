# Changelog - BluOS Loxone Integration

All notable changes and differences compared to the original Bluesound Loxone integration.

## [2.0.0] - 2026-01-05

### 🎯 Complete Rewrite Based on BluOS API v1.7

This version represents a complete rewrite of the original Bluesound integration, expanding from 18 unique commands to **95 comprehensive commands** covering all BluOS API v1.7 capabilities suitable for Loxone automation.

---

## 📊 Comparison Overview

| Feature | Original v1.0 | Enhanced v2.0 | Status |
|---------|---------------|---------------|--------|
| **Total Commands** | 18 unique | 95 | ✅ 5x increase |
| **Presets** | 10 (1-10) | 42 (1-40 + nav) | ✅ 4x increase |
| **Volume Steps** | 2dB only | 0.5dB, 1dB, 2dB, 5dB | ✅ Enhanced |
| **Inputs** | 2 (Optical, BT) | 5 (all types) | ✅ Complete |
| **Queue Management** | Clear only | 5 operations | ✅ Advanced |
| **Power Management** | None | 5 commands | ✅ NEW |
| **Multi-room** | None | 2 commands | ✅ NEW |
| **Advanced Playback** | None | 3 commands | ✅ NEW |
| **Status Queries** | None | 7 commands | ✅ NEW |
| **API Version** | Old format | v1.7 | ✅ Modern |

---

## 🆕 New Features (Not in Original)

### 1. **Advanced Queue Management** (5 commands)
**Original:** Only had "Clear Queue"

**New in v2.0:**
- ✅ `Queue Add URL` - Add tracks/URLs to queue
- ✅ `Queue Delete Track` - Remove specific tracks
- ✅ `Queue Save Playlist` - Save queue as playlist
- ✅ `Queue Move Track` - Reorder tracks in queue
- ✅ `Clear Queue` - Clear entire queue (retained)

### 2. **Power Management** (5 commands)
**Original:** None

**New in v2.0:**
- ✅ `Standby` - Put player in standby mode
- ✅ `Sleep Timer 30min` - Auto-shutoff after 30 minutes
- ✅ `Sleep Timer 60min` - Auto-shutoff after 60 minutes
- ✅ `Sleep Timer 90min` - Auto-shutoff after 90 minutes
- ✅ `Sleep Timer Cancel` - Cancel active sleep timer

### 3. **Multi-Room Grouping** (2 commands)
**Original:** None

**New in v2.0:**
- ✅ `Add Secondary Player` - Create multi-room group
- ✅ `Remove Secondary Player` - Ungroup players

### 4. **Advanced Playback** (3 commands)
**Original:** Basic play/pause only

**New in v2.0:**
- ✅ `Play with Seek` - Start playback at specific position
- ✅ `Play Direct URL` - Play URL directly
- ✅ `Skip with Seek` - Seek to position within track

### 5. **Status Queries** (7 commands)
**Original:** None

**New in v2.0:**
- ✅ `Get Status` - Current player status (XML)
- ✅ `Get Status Long Poll` - Wait for status change (100s timeout)
- ✅ `Get Sync Status` - Synchronized status
- ✅ `Get Sync Status Long Poll` - Wait for sync change
- ✅ `Get Volume` - Current volume level
- ✅ `Get Presets` - List all configured presets
- ✅ `Get Playlist` - Current queue/playlist (100 items)

### 6. **Enhanced Volume Control**
**Original:** Only 2dB steps

**New in v2.0:**
- ✅ `Volume Up/Down 0.5dB` - Fine control
- ✅ `Volume Up/Down 1dB` - Precise control
- ✅ `Volume Up/Down 2dB` - Standard control (retained)
- ✅ `Volume Up/Down 5dB` - Quick adjustment

---

## ✨ Enhanced Existing Features

### Presets
**Original:**
- 10 presets (Preset 1-10)

**Enhanced v2.0:**
- ✅ 40 presets (Preset 1-40)
- ✅ Preset Next - Navigate to next preset
- ✅ Preset Previous - Navigate to previous preset
- **Total: 42 commands vs 10**

### Input Selection
**Original:**
- Optical input (old URL format)
- Bluetooth input (old URL format)

**Enhanced v2.0:**
- ✅ Input Optical - Using modern `inputTypeIndex=spdif-1`
- ✅ Input Coaxial - **NEW**
- ✅ Input Analog - **NEW**
- ✅ Input Bluetooth - Using modern `inputTypeIndex=bluetooth-1`
- ✅ Input HDMI ARC - **NEW**
- **Total: 5 inputs vs 2**

### Bluetooth Modes
**Original:**
- None (basic Bluetooth input only)

**Enhanced v2.0:**
- ✅ Bluetooth Manual Mode - Manual connection required
- ✅ Bluetooth Auto Mode - Auto-play on connect
- ✅ Bluetooth Guest Mode - Auto-disconnect after use
- ✅ Bluetooth Disable - Disable Bluetooth completely
- **Total: 4 modes vs 0**

### Basic Playback Control
**Original:**
- Play, Pause, Stop, Next Track, Previous Track
- Mute Toggle

**Enhanced v2.0:**
- ✅ Play - Retained
- ✅ Pause - Retained
- ✅ Pause Toggle - Retained (using toggle=1 parameter)
- ✅ Stop - Retained
- ✅ Next Track - Retained
- ✅ Previous Track - Retained
- ✅ Mute On - Split from toggle for better control
- ✅ Mute Off - Split from toggle for better control

### Volume Control
**Original:**
- Volume Set (slider 0-100)
- Volume Up 2dB
- Volume Down 2dB

**Enhanced v2.0:**
- ✅ Volume Set - Retained
- ✅ Volume Up/Down: 0.5dB, 1dB, 2dB, 5dB - **4 granularity levels**

### Repeat & Shuffle
**Original:**
- Repeat Off, Repeat All, Repeat Track
- Shuffle On, Shuffle Off

**Enhanced v2.0:**
- ✅ Repeat Off - Retained
- ✅ Repeat Queue - Renamed from "Repeat All" (using state=0)
- ✅ Repeat Track - Retained (using state=1)
- ✅ Shuffle On - Retained
- ✅ Shuffle Off - Retained

---

## 🔧 Technical Improvements

### 1. **Modern API v1.7 Parameters**
**Original:**
- Used old URL-based input selection:
  ```
  /Play?url=Capture%3Ahw%3A1%2C0%2F1%2F25%2F2  (Optical)
  /Play?url=Capture%3Abluez%3Abluetooth         (Bluetooth)
  ```

**Enhanced v2.0:**
- Uses modern `inputTypeIndex` parameter:
  ```
  /Play?inputTypeIndex=spdif-1      (Optical)
  /Play?inputTypeIndex=bluetooth-1  (Bluetooth)
  /Play?inputTypeIndex=coax-1       (Coaxial)
  /Play?inputTypeIndex=analog-1     (Analog)
  /Play?inputTypeIndex=arc-1        (HDMI ARC)
  ```

### 2. **Configurable IP Address**
**Original:**
- Hardcoded IP: `192.168.1.201`

**Enhanced v2.0:**
- Generic placeholder: `192.168.1.100`
- User can easily configure to their network

### 3. **Comprehensive Comments**
**Original:**
- Empty Comment fields

**Enhanced v2.0:**
- Every command has descriptive Comment field
- Explains command purpose and parameters
- Better usability in Loxone Config

### 4. **Organized Structure**
**Original:**
- Random command order

**Enhanced v2.0:**
- Logical grouping by function:
  1. Basic Playback Control
  2. Volume Control
  3. Repeat & Shuffle
  4. Presets
  5. Queue Management
  6. Input Selection
  7. Bluetooth Modes
  8. Advanced Playback
  9. Power Management
  10. Player Grouping
  11. Status Queries
  12. Special Features

### 5. **Proper Addon Metadata**
**Original:**
```json
{
  "name": "bluesound",
  "version": "1.0.0",
  "id": "bluesound-899",
  "file": "bluesound.xml"
}
```

**Enhanced v2.0:**
```json
{
  "name": "bluos-nad-c399",
  "version": "2.0.0",
  "id": "bluos-nad-c399-v2",
  "file": "bluos_nad_c399_enhanced.xml"
}
```

---

## 📋 Command-by-Command Comparison

### Commands Retained (Modified/Improved)
1. ✅ Play
2. ✅ Pause
3. ✅ Stop
4. ✅ Next Track
5. ✅ Previous Track
6. ✅ Volume Set
7. ✅ Volume Up 2dB
8. ✅ Volume Down 2dB
9. ✅ Mute (split into On/Off)
10. ✅ Repeat Off
11. ✅ Repeat Queue (was "Repeat All")
12. ✅ Repeat Track
13. ✅ Shuffle On
14. ✅ Shuffle Off
15. ✅ Presets 1-10 (expanded to 1-40)
16. ✅ Input Optical (using new API)
17. ✅ Input Bluetooth (using new API)
18. ✅ Clear Queue

### Commands Added in v2.0
19. ✅ Pause Toggle
20. ✅ Mute Off (split from toggle)
21. ✅ Volume Up/Down 0.5dB (2 commands)
22. ✅ Volume Up/Down 1dB (2 commands)
23. ✅ Volume Up/Down 5dB (2 commands)
24. ✅ Presets 11-40 (30 commands)
25. ✅ Preset Next
26. ✅ Preset Previous
27. ✅ Queue Add URL
28. ✅ Queue Delete Track
29. ✅ Queue Save Playlist
30. ✅ Queue Move Track
31. ✅ Input Coaxial
32. ✅ Input Analog
33. ✅ Input HDMI ARC
34. ✅ Bluetooth Manual Mode
35. ✅ Bluetooth Auto Mode
36. ✅ Bluetooth Guest Mode
37. ✅ Bluetooth Disable
38. ✅ Play with Seek
39. ✅ Play Direct URL
40. ✅ Skip with Seek
41. ✅ Standby
42. ✅ Sleep Timer 30min
43. ✅ Sleep Timer 60min
44. ✅ Sleep Timer 90min
45. ✅ Sleep Timer Cancel
46. ✅ Add Secondary Player
47. ✅ Remove Secondary Player
48. ✅ Get Status
49. ✅ Get Status Long Poll
50. ✅ Get Sync Status
51. ✅ Get Sync Status Long Poll
52. ✅ Get Volume
53. ✅ Get Presets
54. ✅ Get Playlist

**Total new commands: 77**

---

## 🎯 Use Cases Enabled by v2.0

### Home Automation Scenarios Now Possible:

1. **Multi-Room Audio**
   - Group players for synchronized playback
   - Ungroup for independent zones

2. **Smart Energy Management**
   - Standby mode integration with home presence
   - Sleep timer for bedroom scenarios

3. **Advanced Scheduling**
   - Direct URL playback for alarms/announcements
   - Preset rotation for different times of day

4. **TV Integration**
   - HDMI ARC input for TV audio
   - Automatic input switching

5. **Guest Mode**
   - Bluetooth guest mode for temporary connections
   - Auto-disconnect when done

6. **Playlist Management**
   - Build custom queues
   - Save frequently played combinations

7. **Status Monitoring**
   - Real-time player state tracking
   - Volume level monitoring
   - Playlist visualization

---

## 🔄 Migration Guide

### From Original v1.0 to Enhanced v2.0

1. **Backup** your existing Loxone configuration
2. **Remove** the old Bluesound template
3. **Import** the new BluOS_NAD_C399_v2.lxAddon
4. **Update** the IP address to match your device
5. **Remap** your existing controls:
   - Basic controls work identically
   - Mute Toggle → Use Mute On/Off
   - Repeat All → Use Repeat Queue
   - Add new features as desired

### Compatibility Notes

- ✅ All original commands have equivalents
- ✅ No breaking changes for basic functionality
- ✅ Additional features are opt-in
- ✅ Same API port (11000)
- ✅ Same response format (XML)

---

## 📚 API Version Comparison

| Feature | Original | v2.0 |
|---------|----------|------|
| API Version | Unknown/Old | v1.7 |
| Input Selection | URL-based | inputTypeIndex |
| Long Polling | No | Yes |
| Queue Management | Basic | Advanced |
| Status Queries | No | Yes |
| Multi-room | No | Yes |
| Power Management | No | Yes |

---

## 🙏 Acknowledgments

- **Original integration:** Loxone Bluesound template
- **API documentation:** BluOS Custom Integration API v1.7
- **Testing platform:** NAD C399 with MDC2 BluOS-D module

---

## 📞 Support

For questions or issues specific to v2.0 enhancements, please refer to the GitHub repository.

---

**Last Updated:** 2026-01-05
**Version:** 2.0.0
**Author:** PaulM
