```
# Oppo, OnePlus, Realme SM8650 Universal Kernel Automated Compilation Script
[![STAR](https://img.shields.io/github/stars/cctv18/oppo_oplus_realme_sm8650?style=flat&logo=github)](https://github.com/cctv18/oppo_oplus_realme_sm8650/stargazers)
[![FORK](https://img.shields.io/github/forks/cctv18/oppo_oplus_realme_sm8650?style=flat&logo=greasyfork&color=%2394E61A)](https://github.com/cctv18/oppo_oplus_realme_sm8650/forks)
[![COOLAPK](https://img.shields.io/badge/cctv18_2-cctv18_2?style=flat&logo=android&logoColor=FF4500&label=%E9%85%B7%E5%AE%89&color=FF4500)](http://www.coolapk.com/u/22650293)
[![DISCUSSION](https://img.shields.io/badge/%E8%AE%A8%E8%AE%BA%E5%8C%BA-discussions?logo=livechat&logoColor=FFBBFF&color=3399ff)](https://github.com/cctv18/oppo_oplus_realme_sm8650/discussions)
##### 
A more convenient and faster automated kernel compilation script for OPPO/OnePlus/Realme Snapdragon 8 Gen 3 (SM8650) models.
##### 
The original intention of this project is to solve the following problems:
- The official Green Factory (Oppo/OnePlus/Realme) is slacking off, only open-sourcing part of the code, leading to some kernel code being unable to compile normally with existing configuration XMLs, or even lacking compilation configuration XMLs.
- The official Bazel compiler is too unstable and inefficient, prone to various inexplicable errors, with almost no effective solutions found online, making it extremely unfriendly for newcomers.
- Due to the Green Factory's customized kernel f2fs code, flashing a GKI kernel onto Oppo/OnePlus/Realme devices prevents normal boot unless the data partition is wiped.

## Main Content of This Project
- Provides dual compilation modes: **OKI (Official Kernel Image)** for official source code and **GKI (Generic Kernel Image)** for Google's generic kernel source. OKI is more stable (retains official drivers/scheduling), while GKI offers greater customizability (easier to modify configuration items).
- **Ported the official kernel's f2fs source code to GKI**, allowing GKI kernels to boot normally after flashing while retaining data, just like official OKI kernels, without needing to clear data ~~(create a new folder)~~.
- **Switched to LLVM/Clang 20 for compilation**, and excluded unnecessary vendor source code from the official source. Compared to the original Bazel compiler, this reduces compilation time by nearly half (the original official compiler took over 1 hour per compilation), improves compilation stability, and provides output logs that are easier to maintain and debug.
- **Fixed some bugs/outdated patches in the official code**, and introduced support for Fengchi kernel drivers ~~(to be tested, uncertain if it will work normally)~~.
- Provides **Github Action online compilation** and **shell local compilation** dual-version scripts.
##### 
Due to limited personal energy, this project currently only provides the SukiSU Ultra version KernelSU patch. Support for other KernelSU versions will be updated later ~~(still working on it)~~.

## Already Implemented:
- [x] Oppo/OnePlus/Realme SM8650 Universal A14 OKI Kernel (based on OnePlus 12 6.1.57 A14 official kernel source, suitable for ColorOS 14/RealmeUI 5.0)
##### 
- [x] Oppo/OnePlus/Realme SM8650 Universal A15 OKI Kernel (based on OnePlus 12 6.1.75/6.1.118 A15 official kernel source, suitable for ColorOS 15/RealmeUI 6.0)
##### 
- [x] **Introduced ccache caching**, optimizing the toolchain and compilation process. Subsequent compilation times can be reduced to approximately 6 minutes (Note: The first use of ccache will be slower due to cache creation (about 20 minutes). ccache acceleration will take effect from the second time onwards, accelerating single compilation time to about 6-11 minutes, with specific times fluctuating depending on server load).
##### 
- [x] **Introduced O2 compilation optimization**, improving kernel performance (Caution: If you compiled the kernel and created ccache before updating O2 compilation optimization, please clear the old cache and recompile, otherwise ccache acceleration will not take effect).
##### 
- [x] **Optional manual/kprobes hook mode**: Kprobes hook mode supports switching to sus su mode (similar to Magisk's su implementation, used to ensure compatibility with some applications).
##### 
- [x] **lz4 1.10.0 & zstd 1.5.7 algorithm updates & optimization patches** (from @ferstar, ported by @Xiaomichael)
##### 
- [x] **Optional inclusion of BBR/Brutal and a series of TCP congestion control algorithms**.
##### 
- [x] **Samsung SSG IO scheduler porting**.
##### 
- [x] **Added some network connection performance optimization options**.

## To Be Implemented:
- [ ] Porting full Fengchi kernel support for unofficially supported models (in progress).
- [ ] ZRAM internalization, no need for external zram.ko mounting ~~(Is it still necessary with the new lz4 & zstd patches?)~~.
- [ ] LXC/Docker functionality support.
- [ ] Porting new schedulers for OnePlus series (schedhorizon, etc.).
- [ ] Oppo/OnePlus/Realme SM8650 Universal A14/15 GKI Kernel (porting OnePlus f2fs source to enable flashing without wiping data).
- [ ] Original KernelSU/KernelSU Next support.
- [ ] Integrating multiple kernel compilation scripts into one script.
- More optimizations and feature porting...
##### 
##### 
##### 
## Acknowledgments
- Sukisu Ultra: [SukiSU-Ultra/SukiSU-Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
- susfs4ksu: [ShirkNeko/susfs4ksu](https://github.com/ShirkNeko/susfs4ksu)
- SukiSU Kernel Patch: [SukiSU-Ultra/SukiSU_patch](https://github.com/SukiSU-Ultra/SukiSU_patch)
- GKI Kernel Build Script: [WildKernels/GKI_KernelSU_SUSFS](https://github.com/WildKernels/GKI_KernelSU_SUSFS)
- ~~Localized Kernel Build Script (deprecated): [Suxiaoqinx/kernel_manifest_OnePlus_Sukisu_Ultra](https://github.com/Suxiaoqinx/kernel_manifest_OnePlus_Sukisu_Ultra)~~
- ~~Fengchi Kernel Source (incomplete, under modification): [HanKuCha/sched_ext](https://github.com/HanKuCha/sched_ext)~~
```
