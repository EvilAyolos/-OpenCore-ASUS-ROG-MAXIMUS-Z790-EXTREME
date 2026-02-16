# OpenCore-ASUS-ROG-MAXIMUS-Z790-EXTREME
OpenCore for Asus ROG MAXIMUS Z790 EXTREME + i9-14900KS + REFERENCE CARD AMD 6900 XT

## 🖥 Hardware

<table>
<tr><td>

| Component | Model |
|:----------|:------|
| **CPU**| Intel Core i9-14900KS (24 cores) @ 3.2 GHz |
| **Motherboard** | ASUS ROG MAXIMUS Z790 EXTREME |
| **RAM**| 48GB (2x24GB) G SKILL @ 7400MHz |
| **GPU (Display)**| AMD Radeon RX 6900 XT 16 GB|
| **GPU (Compute)**| NVIDIA GeForce RTX 4090 24GB |
| **Audio**| Realtek ALC4082 |
| **Ethernet**| Intel i226-V 2.5GbE |
| **Ethernet**| AQUANTIA AQC113 10GbE |
| **WiFi/BT**| Intel AX210 (AirportItlwm + OCLP) |
| **Thunderbolt**| Intel Maple Ridge 4C (TB4) |
| **Storage**| 1x Samsung 860 PRO |
| **SMBIOS**  iMacPro1,1 |

</td><td>

### System Info

```
OS:        macOS Sequoia 15.7.4
Kernel:    Darwin 24.6.0 x86_64
OpenCore:  1.0.4
SMBIOS:    iMacPro1,1
```

### PCI Devices

```
GFX0: AMD Radeon RX 6900 XT (Display)
GFX1: RTX 4090 (Compute/NVDAAL)
ETH:  Intel i226-VWIFI: Intel AX210 (OCLP)
ETH2: AQUANTIA AQC113 10GbE
TB4:  Maple Ridge
```

</td></tr>
</table>

---

## ✅ What's Working

| Feature | Status | Notes |
|:--------|:------:|:------|
| **macOS Boot** | ✅ | High Sierra → Sequoia |
| **GPU Acceleration** | ✅ | Metal, QE/CI via RX 570 |
| **Audio** | ✅ | ALC4082 via AppleALC |
| **Ethernet** | ✅ | i226-V via AppleIGC |
| **Ethernet** | ✅ | AQUANTIA AQC113 10GbE|
| **WiFi** | ✅ | Intel AX210 via AirportItlwm + OCLP |
| **Bluetooth** | ✅ | Intel AX210 via IntelBluetoothFirmware |
| **Thunderbolt 4** | ✅ | Hot-plug working |
| **USB Ports** | ✅ | Mapped via USBMap.kext |
| **Sleep/Wake** | ✅ | S3 sleep working |

---

## 📦 Kexts

<details>
<summary><b>Click to expand kext list</b></summary>

| Kext | Version | Description |
|:-----|:-------:|:------------|
| [Lilu](https://github.com/acidanthera/Lilu) | 1.7.2 | Kernel patching framework |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC) | 1.3.8 | SMC emulator |
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC) | 1.3.8 | CPU sensors |
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC) | 1.3.8 | I/O sensors |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen) | 1.7.1 | GPU patching |
| [AppleALC](https://github.com/acidanthera/AppleALC) | 1.9.7 | Audio codec |
| [AppleIGC](https://github.com/SongXiaoXi/AppleIGC) | 1.5 | Intel i226-V ethernet |
| [NVMeFix](https://github.com/acidanthera/NVMeFix) | 1.1.4 | NVMe power management |
| [RestrictEvents](https://github.com/acidanthera/RestrictEvents) | 1.1.7 | Event restrictions |
| [CPUFriend](https://github.com/acidanthera/CPUFriend) | 1.3.1 | CPU power management |
| [CPUFriendDataProvider](https://github.com/corpnewt/CPUFriendFriend) | 1.0.0 | CPU frequency data |
| [CpuTopologyRebuild](https://github.com/b00t0x/CpuTopologyRebuild) | 1.1.0 | CPU topology for P/E cores |
| [USBMap](https://github.com/corpnewt/USBMap) | 1.0 | Custom USB port mapping |
| [USBWakeFixup](https://github.com/osy/USBWakeFixup) | 1.0 | USB wake fixes |
| [NVDAAL](https://github.com/Jnewbon/nvdaal) | 0.1.0 | NVIDIA compute support |
| [AirportItlwm](https://github.com/OpenIntelWireless/itlwm) | 2.3.0 | Intel WiFi native (with OCLP) |
| [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | 2.5.0 | Intel Bluetooth firmware |
| [IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | 2.5.0 | Bluetooth patches |
| [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM) | 2.6.9 | Bluetooth fixes for Monterey+ |

</details>

---

### Boot Arguments

```
watchdog=0 npci=0x3000 -wegnoigpu -ctrsmt -btlfxbeta amfi=0x80
```

| Arg | Description |
|:----|:------------|
| `watchdog=0` | Disable watchdog timer |
| `npci=0x3000` | PCI configuration fix |
| `-wegnoigpu` | Disable iGPU (no iGPU on 13900K) |
| `-ctrsmt` | Raptor Lake SMT compatibility |
| `-btlfxbeta` | Bluetooth fix beta |
| `amfi=0x80` | Allow unsigned kexts (NVDAAL) |

---

## 🚀 Installation

### Prerequisites

- USB drive (16GB+)
- macOS installer
- [ProperTree](https://github.com/corpnewt/ProperTree) for plist editing
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) for serial generation

### Steps

1. **Create USB Installer**
   ```bash
   # Follow Dortania's guide for your macOS version
   ```
   📖 [Creating the USB](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)

2. **Clone this EFI**
   ```bash
   git clone https://github.com/EvilAyolos/-OpenCore-ASUS-ROG-MAXIMUS-Z790-EXTREME
   ```

3. **Copy to USB**
   ```
   Copy EFI/BOOT and EFI/OC to your USB's EFI partition
   ```

4. **Generate SMBIOS** ⚠️ REQUIRED
   ```bash
   # Run GenSMBIOS and select "Generate SMBIOS"
   # Choose model: MacPro7,1
   ```

5. **Edit config.plist**

   Open with ProperTree and set in `PlatformInfo > Generic`:

   | Key | Value |
   |:----|:------|
   | `MLB` | Board Serial from GenSMBIOS |
   | `SystemSerialNumber` | Serial from GenSMBIOS |
   | `SystemUUID` | SmUUID from GenSMBIOS |
   | `ROM` | Your MAC address (no colons) |

6. **Boot and Install!**

> ⚠️ **WARNING**: You MUST generate unique SMBIOS values. Using this repo's serials will cause conflicts and may block your Apple ID.

---

## 📚 Guides

| Guide | Description |
|:------|:------------|
| [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/) | Complete installation guide |
| [OpenCore Post-Install](https://dortania.github.io/OpenCore-Post-Install/) | Post-installation tweaks |
| [GPU Buyers Guide](https://dortania.github.io/GPU-Buyers-Guide/) | Compatible GPUs |
| [ACPI Patching](https://dortania.github.io/Getting-Started-With-ACPI/) | SSDT creation |
| [USB Mapping](https://dortania.github.io/OpenCore-Post-Install/usb/) | USB port configuration |
| [Troubleshooting](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html) | Common issues |

---

## 🌟 Credits

### Bootloader & Drivers
- [OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) - OpenCore bootloader
- [OcBinaryData](https://github.com/acidanthera/OcBinaryData) - HfsPlus.efi

### Kext Developers
- [Acidanthera](https://github.com/acidanthera) - Lilu, VirtualSMC, WhateverGreen, AppleALC, NVMeFix, RestrictEvents, CPUFriend
- [SongXiaoXi](https://github.com/SongXiaoXi) - AppleIGC
- [b00t0x](https://github.com/b00t0x) - CpuTopologyRebuild
- [osy](https://github.com/osy) - USBWakeFixup

### Guides & Community
- [Dortania](https://dortania.github.io/) - OpenCore guides
- [Olarila](https://www.olarila.com/) - ACPI resources
- [Gabriel Maia](https://github.com/gabrielmaialva33) - THANK YOU
---
