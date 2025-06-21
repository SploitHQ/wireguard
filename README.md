# WireGuard

**WireGuard** is a modern, lightweight, and fast VPN protocol designed to be simpler and more secure than older solutions like IPsec and OpenVPN. It uses state-of-the-art cryptography and is built directly into the Linux kernel for performance and minimal attack surface.

🔗 [Use the WireGuard Config Generator on SploitHQ](https://sploithq.com/vpn)

---

## 🔍 What can WireGuard do?

- Create fast and secure VPN tunnels using modern cryptography
- Use simple configuration files for quick setup
- Support roaming and mobile devices with seamless key exchange
- Provide built-in NAT traversal and IPv6 support
- Integrate directly into the OS (Linux kernel module, Windows client, etc.)

---

## ⚙️ Basic Usage

### Bring up a WireGuard interface from config
```
sudo wg-quick up wg0
```

This uses `/etc/wireguard/wg0.conf` or the file specified with `wg-quick`.

---

## 🧰 Commonly Used Commands and Options

| Command / Option            | Description                                                   |
|-----------------------------|---------------------------------------------------------------|
| `wg-quick up <iface>`       | Bring up WireGuard interface using config file                |
| `wg-quick down <iface>`     | Tear down the interface                                       |
| `wg show`                   | Show current WireGuard interface status                       |
| `wg genkey`                 | Generate a private key                                        |
| `wg pubkey`                 | Generate a public key from a private key                      |
| `PrivateKey`                | Private key for local device (inside config)                  |
| `PublicKey`                 | Peer’s public key                                             |
| `AllowedIPs`                | Define traffic routed through the tunnel (e.g. `0.0.0.0/0`)   |
| `Endpoint`                  | IP:Port of the peer (usually server)                          |
| `PersistentKeepalive`       | Interval to send keepalives for NAT traversal                 |

---

## 🧪 Examples

### Generate key pair
```
wg genkey | tee privatekey | wg pubkey > publickey
```

### Sample client configuration (`wg0.conf`)
```
[Interface]
PrivateKey = YOUR_PRIVATE_KEY
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = SERVER_PUBLIC_KEY
Endpoint = vpn.example.com:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

### Bring up the VPN
```
sudo wg-quick up wg0
```

### Tear down the VPN
```
sudo wg-quick down wg0
```

### Check connection status
```
sudo wg show
```

---

## 🌐 Live VPN Config Generator

Want to generate a working WireGuard client config?

👉 [Use the WireGuard Config Generator on SploitHQ](https://sploithq.com/vpn)

- Generate public/private key pairs
- Configure client IP, DNS, server endpoint, and keepalive
- Instantly download a complete `wg0.conf` file

---

## 🔗 Useful Links

- [WireGuard Official Site](https://www.wireguard.com/)
- [WireGuard GitHub Repository](https://github.com/WireGuard)
- [wg-quick Man Page (die.net)](https://linux.die.net/man/8/wg-quick)
- [VPN Tools on SploitHQ](https://sploithq.com/vpn)

---

## 📄 License

This page is maintained by [SploitHQ](https://sploithq.com) and is not affiliated with the WireGuard project.

WireGuard is free and open-source software distributed under the [GPLv2 License](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html).
