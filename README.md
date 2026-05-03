# licheepi-nano-4g-lte

Project build Linux + enable UART1 + PPP for 4G LTE module (SIM A7670C / SIM7600) on LicheePi Nano.

> This project provides configuration for LicheePi Nano SDK.
> To build, you must first setup the official SDK, then apply this repo on top.

---

## 📦 Project structure

This repo only stores configuration:

- Device Tree (DTS)
- Kernel defconfig
- Build scripts
- Rootfs customization

Full SDK (kernel, buildroot, toolchain) is NOT included.

---

## ⚙️ Build environment

```bash
git clone https://github.com/ninhnn2/licheepi_nano_sdk.git
cd licheepi_nano_sdk
./build.sh pull_all

# clone this repo
git clone https://github.com/Minhhaioss/licheepi-nano-4g-lte.git

🔁 Apply config from this repo
cp licheepi-nano-4g-lte/suniv-f1c100s-licheepi-nano.dts Lichee-Pi-linux/arch/arm/boot/dts/
cp licheepi-nano-4g-lte/linux-licheepi_nano_defconfig Lichee-Pi-linux/arch/arm/configs/
⚠️ Always copy DTS and defconfig before building.
Changes in this repo are NOT automatically applied to SDK.

🛠 Build
./build.sh nano_tf

📡 4G LTE (PPP over UART)
UART1 is used for SIM module
DTS mapping:
PA2 → TX
PA3 → RX
Board mapping:
A2 → RX
A3 → TX

PPP must be enabled in kernel config.

✅ Test
ls /dev/ttyS*
cat /dev/ttyS1

🚀 Next steps
AT command test
PPP dial
Auto connect at boot
