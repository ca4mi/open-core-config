#### Parts

| Parts | Name                                                                                         |
| ----- | -------------------------------------------------------------------------------------------- |
| MOBO  | Gigabyte GA-H61M-DS2V Rev 2.0E                                                                |
| CPU   | Intel(R) Core(TM) i5-2300 (4) @ 2.80 GHz                                                     |
| GPU   | NVIDIA GeForce GTX 760 - 2GB                                                                 |
| PSU   | Cooler Master NEX N700                                                                       |
| SSD   | Kingston 240 GB  [TRIM](https://en.wikipedia.org/wiki/Trim_\(computing\)) Enabled via Kernel |
| RAM   | Envinda DDR3 1600 PCI-12800U-CL9 /only works 1333 MHz/                                       |

#### Credits /kexts/

| Kext              | Version |
| ----------------- | ------- |
| Lilu              | V1.7.1  |
| VirtualSMC        | V1.3.7  |
| WhateverGreen     | V1.7.0  |
| AppleALC          | V1.9.5  |
| NVMeFix           | V1.1.3  |
| RestrictEvents    | V1.1.6  |
| SMCProcessor      | V1.3.7  |
| SMCSuperIO        | V1.3.7  |
| CryptexFixup      | V1.0.5  |
| CSLVFixup         | V2.6.1  |
| KDKlessWorkaround | V1.0.0  |
| RSRHelper         | V1.0.0  |
| RealtekRTL8111    | V2.4.2  |
| AMFIPass          | V1.4.1  | 

#### Patching & edits

| Name                                                                                  | Version  |
| ------------------------------------------------------------------------------------- | -------- |
| [OpenCore-Legacy-Patcher (OCLP)](https://github.com/dortania/OpenCore-Legacy-Patcher) | 2.4.1    |
| [OpenCore bootloader](https://github.com/acidanthera/OpenCorePkg)                     | 0.8.8    |
| [OpenCore Auxiliary Tools (OCAT)](https://github.com/ic005k/OCAuxiliaryTools)         | 20250001 |

#### macOS VM for creates installer and bootloader
[dockur/macos](https://github.com/dockur/macos)
docker-compose
 ```yml
services:
  macos:
    image: dockurr/macos
    container_name: macos
    environment:
      VERSION: "12"
      DISK_SIZE: "150G"
      RAM_SIZE: "8G"
      CPU_CORES: "4"
      ARGUMENTS: "-device usb-host,vendorid=0x346d,productid=0x5678"
    devices:
      - /dev/kvm
      - /dev/net/tun
      - "/dev/bus/usb/001/122:/dev/bus/usb/001/122" # usb passthrough
    cap_add:
      - NET_ADMIN
      - SYS_ADMIN
    ports:
      - 8006:8006
      - 5900:5900/tcp
      - 5900:5900/udp
    volumes:
      - ./macos:/storage
    restart: always
    stop_grace_period: 2m
 ```
