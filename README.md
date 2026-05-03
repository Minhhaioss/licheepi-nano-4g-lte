# licheepi-nano-4g-lte

Project build Linux + enable UART1 + PPP for 4G LTE module (SIM A7670C / SIM7600) on LicheePi Nano.

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

## Apply config from this repo
cp suniv-f1c100s-licheepi-nano.dts Lichee-Pi-linux/arch/arm/boot/dts/
cp linux-licheepi_nano_defconfig Lichee-Pi-linux/arch/arm/configs/

🛠 Build
./build.sh nano_tf

## 4G LTE (PPP over UART)
UART1 used for SIM module
Pin mapping:
A2 → RX
A3 → TX

PPP must be enabled in kernel config.

## Test
ls /dev/ttyS*
cat /dev/ttyS1

## Next steps
AT command test
PPP dial
Auto connect at boot