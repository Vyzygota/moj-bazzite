🚀 Personalized Bazzite (NVIDIA Edition)
A custom, atomic gaming OS based on Bazzite, designed for users who refuse to wait for upstream updates. This image is automatically re-baked with the absolute latest technologies available in the Linux ecosystem.

🛠 Key Features
Cutting-Edge Kernel: Always compiled with the latest Linux Kernel (sourced directly from Fedora Rawhide).

Latest NVIDIA Drivers: Pre-installed with the newest NVIDIA proprietary drivers for maximum GPU performance and DLSS support.

Gaming Ready: Includes ProtonGE (via ProtonUp-Qt) and system-level optimizations for handhelds and desktops.

Brave Browser: Pre-configured as a Flatpak for secure, high-performance browsing.

Security: Built-in Kleopatra for advanced GPG/encryption management.

📥 Installation (Rebase)
If you are already on Bazzite or any Fedora-based atomic desktop, you can switch to this image with a single command:

Bash
rpm-ostree rebase ostree-unverified-registry:ghcr.io/vyzygota/moj-bazzite:latest
⚙️ Build System
This repository uses BlueBuild to ensure a consistent, reliable, and reproducible build process via GitHub Actions. Every update to this repository triggers a fresh build with the newest available packages.

Pro-tip do "About" na boku repozytorium:
W prawym górnym rogu GitHuba, w sekcji About, wklej krótki, "mięsisty" opis:

⚡ Custom Bazzite image with latest Fedora Rawhide Kernel and newest NVIDIA drivers. Includes Brave, Kleopatra, and ProtonGE optimizations.


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
