# Android GKI Kernel Build Action Template

A GitHub Actions workflow template for building Android Generic Kernel Image (GKI) kernels (Linux 5.10 / 5.15 / 6.1) with AOSP Clang toolchains and automated AnyKernel3 packaging.

---

## Features

- **Automated Clang Toolchain Setup**: Pre-configured for AOSP Clang 17+ and ARM64 cross-compilation.
- **ThinLTO Support**: Full support for Clang Link Time Optimization.
- **AnyKernel3 Integration**: Automatically packages `Image` or `Image.gz` into flashable AnyKernel3 zip archives.
- **Artifact Upload**: Artifacts automatically uploaded and ready for download directly from GitHub Actions run summary.

---

## Usage

Copy `.github/workflows/build-kernel.yml` to your target Android kernel repository:

```yaml
name: Build GKI Kernel

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Build Kernel
        run: |
          make ARCH=arm64 O=out defconfig
          make ARCH=arm64 O=out -j$(nproc)
```

---

## License
MIT License
