<div align="center">

<img src="snap/gui/qrcp.png" alt="qrcp logo" width="128" />

# qrcp

**Transfer files over Wi-Fi with a QR code**

[![qrcp](https://snapcraft.io/qrcp/badge.svg)](https://snapcraft.io/qrcp)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [qrcp](https://github.com/claudiodangelis/qrcp), a command-line tool that transfers files between your computer and your phone over the local network.

</div>

---

## Getting Started

<a href="https://snapcraft.io/qrcp"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install qrcp
qrcp send ~/Pictures/photo.jpg
```

Scan the QR code printed in the terminal with your phone to download the file. To upload files from the phone instead:

```bash
qrcp receive --output ~/Downloads
```

Both devices must be on the same network. Directories and multiple files are sent as a zip archive; add `--zip` to compress a single file too.

## Configure

qrcp has no snap options. Pass flags on each run, or save defaults with the interactive wizard:

```bash
qrcp config
qrcp --interface wlan0 --port 8080 send video.mp4
qrcp --secure --tls-cert ~/cert.pem --tls-key ~/key.pem send notes.txt
```

The configuration is stored in `~/snap/qrcp/current/.config/qrcp/config.yml`. Run `qrcp --help` for every flag.

For `/media` or `/mnt`, connect `sudo snap connect qrcp:removable-media`.

## Limitations

- Hidden files directly under your normal home directory are inaccessible.
- Your firewall must allow incoming connections on the chosen port. Set a fixed port with `--port` to open it once.
- An existing `~/.config/qrcp` from a non-snap install is not used; run `qrcp config` again, or copy the file to a non-hidden folder in your home and pass it with `--config`.

## Build

```bash
git clone https://github.com/sidalit/qrcp-snap.git
cd qrcp-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/qrcp-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/claudiodangelis/qrcp/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/qrcp-snap/blob/main/LICENSE).
