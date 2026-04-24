# 🚀 Personalized Bazzite Deck (NVIDIA Edition)

A custom, atomic gaming OS based on Bazzite, designed for gamers and power-users who demand cutting-edge performance. This image combines the streamlined console-like interface of Steam Deck with hardware-accelerated drivers tailored specifically for NVIDIA systems.

_**⚡ Engineered with Google Gemini:** This repository's architecture, including its custom kernel build pipeline and deployment strategies, was co-created with the **Gemini AI Agent (Antigravity)** to ensure maximum stability and zero-day module injection._

## 🎮 Key Features

*   **Console-Level Experience:** Based on bazzite-deck-nvidia, bringing the seamless Gamescope (SteamUI) console interface natively to your NVIDIA-powered machine.
*   **Zero-Day NVIDIA Drivers:** Built via an independent CI/CD pipeline (akmods-nvidia-custom) fetching the bleeding-edge NVIDIA proprietary drivers so you get maximum FPS and DLSS support without waiting for upstream updates.
*   **Surgical Module Injection:** Automatically extracts your custom *.ko modules and wires them precisely into the current Linux kernel via depmod, preserving atomic OS integrity.
*   **Gaming Ready Out-of-the-Box:** Includes ProtonGE (via ProtonUp-Qt), Brave Browser as Flatpak, Kleopatra for security, and system-level optimizations for modern gaming on desktop and handhelds.
*   **Immutable & Bulletproof:** Powered by BlueBuild and rpm-ostree. If an update breaks, you can instantly roll back to the previous snapshot.

## 📥 Installation

Ready to unleash your GPU? Rebase your Fedora/Bazzite installation instantly:

```bash
rpm-ostree rebase ostree-unverified-registry:ghcr.io/vyzygota/moj-bazzite:latest
```
Reboot your machine, and you're fully geared up.

---

# BlueBuild Template &nbsp; [![bluebuild build badge](https://github.com/blue-build/template/actions/workflows/build.yml/badge.svg)](https://github.com/blue-build/template/actions/workflows/build.yml)

See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.

After setup, it is recommended you update this README to describe your custom image.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/blue-build/template:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/blue-build/template:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/how-to/generate-iso/#_top). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/blue-build/template
```
