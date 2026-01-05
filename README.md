# BluOS Loxone Integration v2.0

Complete Loxone integration for BluOS-enabled devices based on BluOS Custom Integration API v1.7.

Specifically designed and tested for **NAD C399** amplifier with **MDC2 BluOS-D** module.

## 🇳🇱 Nederlands | 🇬🇧 English

---

## 🇳🇱 **Nederlandse Documentatie**

### Overzicht

Deze uitgebreide Loxone-integratie biedt volledige controle over BluOS-apparaten via de BluOS Custom Integration API v1.7. Deze addon is specifiek ontwikkeld voor de NAD C399 versterker met MDC2 BluOS-D module, maar werkt met alle BluOS-compatibele apparaten.

### Functies

#### ✅ **Basisbesturing** (6 commando's)
- Afspelen, Pauzeren, Pauzeren Toggle, Stoppen
- Volgend nummer, Vorig nummer

#### ✅ **Volume controle** (11 commando's)
- Volume instellen (0-100% slider)
- Volume verhogen/verlagen: 0.5dB, 1dB, 2dB, 5dB stappen
- Dempen aan/uit

#### ✅ **Afspeelmodi** (5 commando's)
- Herhalen: Uit, Wachtrij, Nummer
- Willekeurig: Aan, Uit

#### ✅ **Presets** (42 commando's)
- Alle 40 presets (1-40)
- Volgend/vorig preset

#### ✅ **Wachtrijbeheer** (5 commando's) - **NIEUW**
- Wachtrij wissen
- URL toevoegen aan wachtrij
- Nummer verwijderen uit wachtrij
- Wachtrij opslaan als afspeellijst
- Nummer verplaatsen in wachtrij

#### ✅ **Ingang selectie** (5 commando's)
- Optisch (SPDIF)
- Coaxiaal
- Analoog
- Bluetooth
- HDMI ARC

#### ✅ **Bluetooth modi** (4 commando's)
- Handmatig, Automatisch, Gast, Uitschakelen

#### ✅ **Geavanceerd afspelen** (3 commando's) - **NIEUW**
- Afspelen met seek (start op specifieke positie)
- Directe URL afspelen
- Skip met seek (zoek binnen nummer)

#### ✅ **Energiebeheer** (5 commando's) - **NIEUW**
- Standby modus
- Slaaptimer: 30, 60, 90 minuten
- Slaaptimer annuleren

#### ✅ **Multi-room groepering** (2 commando's) - **NIEUW**
- Secundaire speler toevoegen aan groep
- Secundaire speler verwijderen uit groep

#### ✅ **Status queries** (7 commando's)
- Status ophalen
- Status met long polling (wacht op wijziging)
- Sync status ophalen
- Sync status met long polling
- Volume ophalen
- Presets ophalen
- Afspeellijst ophalen

#### ✅ **Speciale functies** (1 commando)
- Deurbel chime

**Totaal: ~95 commando's** (vs 18 in originele versie)

### Installatie

1. **Download** het bestand `BluOS_NAD_C399_v2.lxAddon`
2. **Importeer** in Loxone Config via: *Bestand → Bibliotheek → Sjablonen importeren*
3. **Sleep** het sjabloon naar uw virtuele uitgangen
4. **Configureer** het IP-adres van uw BluOS-apparaat:
   - Standaard: `http://192.168.1.100:11000`
   - Wijzig `192.168.1.100` naar uw apparaat IP
   - Poort `11000` is de standaard BluOS API poort

### Configuratie

#### IP-adres instellen
Na het importeren, pas het **Address** veld aan in het VirtualOut element:
```
http://[UW_BLUOS_IP]:11000
```

Bijvoorbeeld voor IP 192.168.8.46:
```
http://192.168.8.46:11000
```

#### Veel gebruikte commando's

**Basis afspelen:**
- `Play` - Start afspelen
- `Pause` - Pauzeer
- `Stop` - Stop afspelen

**Volume:**
- `Volume Set` - Stel volume in met slider (0-100%)
- `Volume Up/Down 2dB` - Standaard volume aanpassing
- `Mute On/Off` - Dempen aan/uit

**Ingangen:**
- `Input Optical` - Optische ingang (NAD C399 SPDIF)
- `Input Coaxial` - Coaxiale ingang
- `Input Analog` - Analoge ingang
- `Input Bluetooth` - Bluetooth ingang
- `Input HDMI ARC` - HDMI ARC (voor TV)

**Presets:**
- `Preset 1` t/m `Preset 40` - Direct preset selectie
- `Preset Next/Previous` - Navigeer door presets

### API Versie

Deze integratie is gebaseerd op **BluOS Custom Integration API v1.7** en bevat alle beschikbare functies voor Loxone automation doeleinden.

### Compatibiliteit

- **Loxone Miniserver** versie 12.2.1.2 of hoger
- **BluOS** apparaten met API v1.7 ondersteuning
- Getest op **NAD C399** met **MDC2 BluOS-D** module
- Compatibel met andere BluOS-apparaten (Bluesound, NAD, etc.)

### Verschillen met originele versie

Zie [CHANGELOG.md](CHANGELOG.md) voor een volledige lijst van verschillen ten opzichte van de originele Bluesound integratie.

**Belangrijkste verbeteringen:**
- ✅ 95 commando's vs 18 in origineel
- ✅ Alle 40 presets (was 10)
- ✅ Geavanceerd wachtrijbeheer
- ✅ Energiebeheer (standby, slaaptimer)
- ✅ Multi-room groepering
- ✅ Meer volume stappen (0.5dB, 5dB)
- ✅ Status long polling
- ✅ Alle 5 ingangen (was 2)
- ✅ Moderne API v1.7 parameters

---

## 🇬🇧 **English Documentation**

### Overview

This comprehensive Loxone integration provides complete control over BluOS devices using the BluOS Custom Integration API v1.7. Specifically designed for the NAD C399 amplifier with MDC2 BluOS-D module, but compatible with all BluOS-enabled devices.

### Features

#### ✅ **Basic Playback Control** (6 commands)
- Play, Pause, Pause Toggle, Stop
- Next Track, Previous Track

#### ✅ **Volume Control** (11 commands)
- Volume Set (0-100% slider)
- Volume Up/Down: 0.5dB, 1dB, 2dB, 5dB steps
- Mute On/Off

#### ✅ **Playback Modes** (5 commands)
- Repeat: Off, Queue, Track
- Shuffle: On, Off

#### ✅ **Presets** (42 commands)
- All 40 presets (1-40)
- Preset Next/Previous

#### ✅ **Queue Management** (5 commands) - **NEW**
- Clear Queue
- Add URL to Queue
- Delete Track from Queue
- Save Queue as Playlist
- Move Track in Queue

#### ✅ **Input Selection** (5 commands)
- Optical (SPDIF)
- Coaxial
- Analog
- Bluetooth
- HDMI ARC

#### ✅ **Bluetooth Audio Modes** (4 commands)
- Manual, Auto, Guest, Disable

#### ✅ **Advanced Playback** (3 commands) - **NEW**
- Play with Seek (start at specific position)
- Play Direct URL
- Skip with Seek (seek within track)

#### ✅ **Power Management** (5 commands) - **NEW**
- Standby Mode
- Sleep Timer: 30, 60, 90 minutes
- Cancel Sleep Timer

#### ✅ **Multi-Room Grouping** (2 commands) - **NEW**
- Add Secondary Player to Group
- Remove Secondary Player from Group

#### ✅ **Status Queries** (7 commands)
- Get Status
- Get Status with Long Polling (waits for change)
- Get Sync Status
- Get Sync Status with Long Polling
- Get Volume
- Get Presets
- Get Playlist

#### ✅ **Special Features** (1 command)
- Doorbell Chime

**Total: ~95 commands** (vs 18 in original)

### Installation

1. **Download** the file `BluOS_NAD_C399_v2.lxAddon`
2. **Import** into Loxone Config via: *File → Library → Import Templates*
3. **Drag** the template to your virtual outputs
4. **Configure** the IP address of your BluOS device:
   - Default: `http://192.168.1.100:11000`
   - Change `192.168.1.100` to your device IP
   - Port `11000` is the default BluOS API port

### Configuration

#### Setting the IP Address
After importing, adjust the **Address** field in the VirtualOut element:
```
http://[YOUR_BLUOS_IP]:11000
```

For example, for IP 192.168.8.46:
```
http://192.168.8.46:11000
```

#### Commonly Used Commands

**Basic Playback:**
- `Play` - Start playback
- `Pause` - Pause playback
- `Stop` - Stop playback

**Volume:**
- `Volume Set` - Set volume with slider (0-100%)
- `Volume Up/Down 2dB` - Standard volume adjustment
- `Mute On/Off` - Mute/Unmute

**Inputs:**
- `Input Optical` - Optical input (NAD C399 SPDIF)
- `Input Coaxial` - Coaxial input
- `Input Analog` - Analog input
- `Input Bluetooth` - Bluetooth input
- `Input HDMI ARC` - HDMI ARC (for TV)

**Presets:**
- `Preset 1` through `Preset 40` - Direct preset selection
- `Preset Next/Previous` - Navigate through presets

### API Version

This integration is based on **BluOS Custom Integration API v1.7** and includes all available features suitable for Loxone automation purposes.

### Compatibility

- **Loxone Miniserver** version 12.2.1.2 or higher
- **BluOS** devices with API v1.7 support
- Tested on **NAD C399** with **MDC2 BluOS-D** module
- Compatible with other BluOS devices (Bluesound, NAD, etc.)

### Differences from Original Version

See [CHANGELOG.md](CHANGELOG.md) for a complete list of differences compared to the original Bluesound integration.

**Key Improvements:**
- ✅ 95 commands vs 18 in original
- ✅ All 40 presets (was 10)
- ✅ Advanced queue management
- ✅ Power management (standby, sleep timer)
- ✅ Multi-room grouping
- ✅ More volume steps (0.5dB, 5dB)
- ✅ Status long polling
- ✅ All 5 inputs (was 2)
- ✅ Modern API v1.7 parameters

---

## Technical Details

### File Structure

```
BluOS_NAD_C399_v2.lxAddon
├── desc.json                        # Addon descriptor
└── bluos_nad_c399_enhanced.xml      # Virtual output template
```

### API Endpoints Used

This integration uses the following BluOS API endpoints:

**Playback Control:**
- `/Play`, `/Pause`, `/Stop`, `/Skip`, `/Back`

**Volume:**
- `/Volume?level=<0-100>`
- `/Volume?db=<+/- dB>`
- `/Volume?mute=<0|1>`

**Modes:**
- `/Repeat?state=<0|1|2>`
- `/Shuffle?state=<0|1>`

**Presets:**
- `/Preset?id=<1-40|+1|-1>`

**Queue:**
- `/Clear`, `/Add`, `/Delete`, `/Save`, `/Move`

**Inputs:**
- `/Play?inputTypeIndex=<spdif-1|coax-1|analog-1|bluetooth-1|arc-1>`

**Bluetooth:**
- `/audiomodes?bluetoothAutoplay=<0|1|2|3>`

**Power:**
- `/Standby`
- `/Sleep?timeout=<minutes>`

**Grouping:**
- `/AddSlave?slave=<IP>`
- `/RemoveSlave?slave=<IP>`

**Status:**
- `/Status`, `/SyncStatus`, `/Volume`, `/Presets`, `/Playlist`
- `/Status?timeout=<seconds>` (long polling)

**Special:**
- `/Doorbell?play=1`

### Default Port

BluOS API default port: **11000**

### Response Format

All API responses are in XML format. Status queries return detailed XML with current player state.

## Support

For issues, questions, or contributions, please open an issue on GitHub.

## License

This integration is provided as-is, free to use and modify.

## Credits

- **Original Bluesound integration:** Loxone library
- **Enhanced version:** Based on BluOS Custom Integration API v1.7
- **Developed for:** NAD C399 with MDC2 BluOS-D module
- **API Documentation:** BluOS Custom Integration API v1.7

## Version History

- **v2.0.0** (2026-01-05) - Complete rewrite based on API v1.7
- **v1.0.0** - Original Bluesound integration

---

**Enjoy your enhanced BluOS Loxone integration!** 🎵
