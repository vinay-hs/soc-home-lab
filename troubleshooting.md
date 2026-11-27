# Troubleshooting

## 1. VMs could not reach each other
**Problem:** Kali was attached to "NAT", so it was isolated from other VMs.
**Cause:** With plain NAT, every VM gets its own private network.
**Fix:** Created a NAT Network `soclab` (10.0.2.0/24) and attached all VMs to it.
The "NAT Network" option only shows in VirtualBox **Expert** settings mode.

    VBoxManage natnetwork add --netname soclab --network "10.0.2.0/24" --enable --dhcp on

## 2. Kernel panic when booting the Ubuntu installer
**Problem:** `Kernel panic - not syncing: Fatal exception in interrupt`
**Fix:** In VM settings: 2 CPUs, enabled PAE/NX, enabled I/O APIC,
Paravirtualization Interface = Default.

## 3. Installer stuck at "Loading essential drivers"
**Fix:** Increased video memory from 16 MB to 128 MB (VMSVGA, 3D acceleration off).

## 4. Only half the disk used by default
**Fix:** Unticked "Set up this disk as an LVM group" in the installer,
so the root partition uses the full 50 GB (Wazuh stores a lot of log data).

## 5. Forgot the login username
**Cause:** German keyboard layout (QWERTZ) during install.
**Fix:** GRUB → Advanced options → recovery mode → root shell:

    mount -o remount,rw /
    ls /home          # shows the real username
    passwd <username> # reset password if needed

## 6. Low host RAM
**Problem:** 16 GB host with ~12 GB already used by Windows.
**Fix:** Wazuh VM 4 GB, Kali 2 GB, run only two VMs at a time,
used the `-i` flag on the Wazuh installer to skip the hardware check.
