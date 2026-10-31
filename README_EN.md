<!-- 作者 shingja · github.com/shingja/shingja-steam-ipv6-accelerator · PolyForm Noncommercial 1.0.0 · 保留版权标识⁠​‌‌‌​​‌‌​‌‌​‌​​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌‌‌​‌‌​‌​‌​​‌‌​​​​‌​​‌​‌‌‌‌​‌‌‌​​‌‌​‌‌​‌​​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌‌‌​‌‌​‌​‌​​‌‌​​​​‌​​‌​‌‌​‌​‌‌‌​​‌‌​‌‌‌​‌​​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​‌‌​‌​​‌​‌‌​‌​‌‌​‌​​‌​‌‌‌​​​​​‌‌‌​‌‌​​​‌‌​‌‌​​​‌​‌‌​‌​‌‌​​​​‌​‌‌​​​‌‌​‌‌​​​‌‌​‌‌​​‌​‌​‌‌​‌‌​​​‌‌​​‌​‌​‌‌‌​​‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​‌‌‌‌​‌‌‌​​‌​​​‌​‌‌‌‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​‌‌​​​‌​‌‌‌‌​‌‌‌​‌‌​​​‌‌​​​‌⁠ -->

# USTB Campus IPv6 Steam Download Accelerator

**Make Steam downloads use campus IPv6 instead of IPv4.**

A small Windows tool for the USTB campus network / CERNET2 environment. It does not modify the Steam client, inject into processes, or touch game files. It only adds a reversible hosts block and a loopback relay.

> **Official repository**: https://github.com/shingja/shingja-steam-ipv6-accelerator
>
> This is the **public** version of the project.

> Copyright belongs to shingja. Noncommercial use is free; redistribution must keep attribution and the license. Commercial use, false claims of originality, and implied endorsement are prohibited. See [NOTICE.md](NOTICE.md).

> **Unofficial project**: not affiliated with, endorsed by, or connected to the University of Science and Technology Beijing, Valve, or Steam. Check your campus network policy before use.

> **Learning-purpose notice**: this project is for studying IPv6, DNS, hosts, TCP forwarding, and security engineering. It is **not** a tool for bypassing campus authentication, billing, traffic management, or account sharing. Resale, paid download proxying, and commercial use are prohibited. See [docs/10-使用边界与合规.md](docs/10-使用边界与合规.md).

## What it does

Steam on campus often downloads over IPv4 even when IPv6 is available, and campus DNS may not return AAAA records for CDN domains. This tool:

1. Gets the current Steam content CDN domains from Steam's official API (plus a fallback list).
2. Resolves their IPv6 addresses through multiple public IPv6 DNS servers.
3. Probes candidates and picks reachable nodes.
4. Maps each working domain to a loopback address in `hosts`.
5. Runs a local relay on `127.0.0.20:80` and forwards to the CDN's IPv6 node.

Steam sees a local IPv4 connection, while the actual download traffic leaves over IPv6.

## Requirements

- Windows 10 / 11
- Python 3.9+ with `python.exe` on PATH
- Campus IPv6 / CERNET2 connectivity
- Administrator rights for the hosts file

## Quick start

1. Double-click `SteamIPv6Accelerator-v1.0.0.exe`.
2. Choose `1`.
3. Disable the system proxy if prompted (Clash and similar proxies force Steam to use IPv4).
4. Wait 10–40 seconds for DNS resolution and probing.
5. Restart Steam, then start a download.
6. Keep the window open. Press Enter after the download to stop and restore `hosts`.

If the program is killed and `hosts` is not restored, run 菜单 `2` or:

```bat
SteamIPv6Accelerator-v1.0.0.exe --restore
```


## Limitations

- Windows only.
- Steam download CDN only; no web proxy or game-network acceleration.
- Some secondary CDN domains have no IPv6 node and remain on IPv4.
- Speed is not guaranteed.
- Does not bypass authentication, billing, or campus network policy.

## License

PolyForm Noncommercial License 1.0.0. See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md).

## Author

- GitHub: [@shingja](https://github.com/shingja)
- Email: [gy79790920@126.com](mailto:gy79790920@126.com)

---

<sub>© 2026 shingja · PolyForm Noncommercial 1.0.0 · Unofficial project</sub>
