# Display Issue on Ubuntu 24.04 with kernel 6.8

## Problem Description

On Ubuntu 24.04 LTS with kernel 6.8 (specifically 6.8.0-52.53~22.04.1), a major display issue occurs when booting the system.

### Symptoms
- Black screen at startup
- No brightness control
- Need to use recovery mode to access the system

## Hardware Configuration
- Lenovo Yoga Pro 7 14ASP9
- Processor: AMD Ryzen AI 9 365
- Integrated Graphics Card: AMD Radeon 880M

## Working Solution

### 1. Upgrade to kernel 6.12 LTS

```bash
sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update
sudo apt install mainline
sudo mainline install-latest
```

After installation, restart the system.

---

### 2. Switch from Wayland to X11 (to resolve lags)

Edit the GDM configuration file:
```bash
sudo nano /etc/gdm3/custom.conf
```

Uncomment (remove the `#`) the following line to disable Wayland:
```
WaylandEnable=false
```

Restart the system or the GDM service:
```bash
sudo systemctl restart gdm3
```

---
---

This README documents a personal troubleshooting experience. Solutions may vary depending on the exact hardware configuration and operating system version.
Thanks to perplexity for that.
