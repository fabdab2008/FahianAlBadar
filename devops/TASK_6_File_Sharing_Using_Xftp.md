# TASK 6: File Sharing Using Xftp

To share files using **Xftp** between two **Ubuntu VMs** (on VMware, possibly on different physical machines), follow these steps:

---

## Prerequisites

- Xftp installed on your host or your friend's host (Windows).
- Ubuntu VMs set up in VMware on both devices.
- SSH server running on the Ubuntu VM(s).
- Network connectivity between both machines (use **Bridged** or **Host-Only** networking in VMware).

---

## Step-by-Step Guide: File Sharing via Xftp

### Step 1: Install and Enable SSH on Ubuntu

On both VMs (your Ubuntu and your friend’s), open terminal and run:

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
```

> This allows incoming SSH connections, which Xftp uses.

---

### Step 2: Find the IP Address of the Ubuntu VM

In each Ubuntu VM, run:

```bash
ip a
```

Look for an IP address like `192.168.x.x` under `eth0` or `ens33`.

---

### Step 3: Configure VMware Network Settings (if needed)

To make both Ubuntu VMs visible to each other:

- In **VMware > Settings > Network Adapter**:
  - Set to **Bridged** or **Host-Only** mode.

**Bridged**:  
VMs will be on the same network as your router (ideal for cross-device communication).

**Host-only**:  
Useful if both VMs are on the same physical host.

---

### Step 4: Use Xftp to Connect to the Remote Ubuntu VM

- Open **Xftp** on your host machine.
- Click **File > New > SFTP Session**.
- Enter the following:

  - **Host**: IP address of the friend's Ubuntu VM  
  - **Port**: 22 (default SSH port)  
  - **Username**: `ubuntu` or whatever your friend's username is  
  - **Password**: That user's password

- Click **Connect**.

---

### Step 5: Transfer Files

Use the left/right panes in Xftp to drag and drop files:

- From your Ubuntu to your friend’s Ubuntu.
- Or vice versa.

> Xftp supports both upload and download over SFTP.

---

## Optional: Transfer Without Xftp

If both VMs are Ubuntu, you can also use `scp` (secure copy):

```bash
scp filename user@remote_ip:/home/user/
```

**Example**:

```bash
scp myfile.txt friend@192.168.1.20:/home/friend/
```

---

## Troubleshooting Tips

| Problem                | Solution                                                |
|------------------------|----------------------------------------------------------|
| Can’t connect via Xftp | Ensure SSH server is running and firewall allows port 22 |
| IP address not visible | Set VMware to Bridged/Host-Only                          |
| Auth fails in Xftp     | Use correct Ubuntu username/password                     |
| Still blocked?         | Temporarily disable firewall: `sudo ufw disable`         |
