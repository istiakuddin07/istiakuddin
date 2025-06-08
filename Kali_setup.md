# Kali Linux on VirtualBox: My Setup Guide 🖥️🔓

   *Tested on Windows 11/10 with VirtualBox 7.0+ and Kali Linux 2024.2*

   ## **My Current Setup**
   - **Host OS**: Windows 11  
   - **Virtualization**: Oracle VirtualBox 7.0+  
   - **Kali Version**: Rolling Release (2024.2)  
   - **Resources Allocated**: 4GB RAM, 50GB Storage, 2 CPU Cores  

   ---

   ## **Why This Combo?**
   ✅ **Safe for pentesting** (isolated from host OS)  
   ✅ **Easy to snapshot/reset** after experiments  
   ✅ **No driver issues** (unlike bare-metal installs)  

   ---

   ## **Step-by-Step Installation**
   ### 1. **Download & Verify**
   ```bash
   # Official Kali VM Image (Pre-configured for VirtualBox):
   wget https://kali.download/virtual-images/kali-2024.2/kali-linux-2024.2-virtualbox-amd64.7z
   sha256sum kali-linux-2024.2-virtualbox-amd64.7z  # Verify checksum!
   ```

   ### 2. **Import to VirtualBox**
   1. Extract the `.7z` file  
   2. Open VirtualBox → **File** → **Import Appliance**  
   3. Select the `.ova` file and allocate resources (I use **4GB RAM + 2 CPUs**)  

   ### 3. **First Boot**
   - **Credentials**: `kali:kali`  
   - **Network**: Use **Bridged Adapter** for LAN access or **NAT** for host-only.  

   ---

   ## **Post-Install Tweaks (What I Did)**
   ### 🔄 Update System
   ```bash
   sudo apt update && sudo apt full-upgrade -y
   sudo apt install -y kali-linux-headless  # Minimal tools (~1.5GB)
   ```

   ### 🛠️ Fix Common Issues
   - **Screen Resolution**:  
     ```bash
     sudo apt install -y virtualbox-guest-utils
     sudo reboot
     ```
   - **Shared Clipboard**:  
     VirtualBox Settings → **General** → **Advanced** → Enable **Bidirectional** clipboard.  

   ### 📦 My Favorite Preinstalled Tools
   | Tool          | Command              | Use Case                     |
   |---------------|----------------------|------------------------------|
   | `nmap`        | `nmap -sV <IP>`      | Network scanning             |
   | `sqlmap`      | `sqlmap -u <URL>`    | SQL injection testing        |
   | `msfconsole`  | `msfconsole`         | Metasploit framework         |

   ---

   ## **Pro Tips from My Experience**
   1. **Take Snapshots** before risky operations (*VirtualBox → Machine → Take Snapshot*).  
   2. **Disable Sleep Mode** in Kali to avoid interruptions during scans:  
      ```bash
      sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
      ```
   3. **Keyboard Shortcuts**:  
      - `Host (Right Ctrl) + C` – Copy from VM  
      - `Host + D` – Switch to seamless mode  

   ---

   🚩 **Warning**: Always use Kali ethically! Unauthorized testing is illegal.
🔗 **Official Docs**: [Kali VirtualBox Docs](https://www.kali.org/docs/virtualization/install-virtualbox-guest-vm/)
