# ThinkPad T14 Hackintosh

EFI de OpenCore 1.0.7 para una Lenovo ThinkPad T14 Gen 1 (Intel) con macOS Sequoia 15.7.5, en arranque dual con Windows en el mismo disco.

## Equipo

| Parte | Detalle |
| --- | --- |
| Modelo | Lenovo ThinkPad T14 Gen 1 (Intel) |
| Procesador | Intel Core i7-10610U, 4 núcleos y 8 hilos (Comet Lake) |
| Gráficos | Intel UHD Graphics 620 |
| Pantalla | 14 pulgadas, 1920 × 1080, táctil (ELAN, por VoodooI2CHID) |
| Memoria | 24 GB |
| Disco | Kingston NV2 de 1 TB (NVMe), mitad macOS y mitad Windows |
| Audio | Realtek ALC257 (`alcid=86`) |
| Ethernet | Intel I219-LM (IntelMausi) |
| Wi-Fi y Bluetooth | Intel AX201 (AirportItlwm, IntelBluetoothFirmware) |
| Trackpad y TrackPoint | Synaptics por SMBus (VoodooRMI) |
| Teclado | Retroiluminado; teclas de función y luz con YogaSMC y BrightnessKeys |
| Cámara | Integrada (Chicony, USB) |
| Lector de tarjetas | Realtek (RealtekCardReader) |
| Batería | Lectura de carga y ciclos con SMCBatteryManager |
| SMBIOS | `MacBookPro16,2` |

## Qué incluye

- **ACPI:** 20 tablas SSDT para batería, teclas de función, brillo, reposo, USB y el controlador embebido de la ThinkPad.
- **Energía:** CPUFriend con su perfil, CpuTscSync y NVMeFix.
- **Teclado y trackpad:** VoodooPS2, VoodooRMI, VoodooI2C y VoodooSMBus.
- **Funciones de ThinkPad:** YogaSMC, BrightnessKeys, ECEnabler y SMCBatteryManager.
- **Red:** IntelMausi, AirportItlwm, IntelBluetoothFirmware, IntelBTPatcher y BlueToolFixup.
- **Lector de tarjetas:** RealtekCardReader.
- **Puertos USB:** mapa propio en `USBPorts.kext`.

## Antes de usarla

El `config.plist` viene **sin números de serie**. En `PlatformInfo > Generic` debes poner los tuyos:

1. Genera un juego para `MacBookPro16,2` con [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2. Llena `SystemSerialNumber`, `MLB` y `SystemUUID`.
3. Pon en `ROM` la dirección MAC de tu tarjeta de red.

En `Misc > Entries` hay una entrada de Windows que apunta a la partición de este equipo. Bórrala o cámbiala por la tuya.

## Advertencia

Es la configuración de un equipo concreto. Si tu hardware o tu versión de BIOS difieren, úsala como referencia y sigue la [guía de Dortania](https://dortania.github.io/OpenCore-Install-Guide/). Haz respaldo de tu EFI actual antes de reemplazarla.
