# FreeBSD installation 

on UTM (Apple Silicon).
from zero to booted system.

---

## host

- macOS (Apple Silicon)
- UTM installed (`brew install --cask utm`)

---

## 1. download ISO

use the **installer**, not VM images.

1. go to https://www.freebsd.org/where/
2. scroll to **Installer Images**
3. select **aarch64** architecture
4. download `FreeBSD-15.0-RELEASE-arm64-aarch64-disc1.iso`

---

## 2. create VM in UTM

1. open UTM
2. click **Create a New Virtual Machine**
3. select **Virtualize**
4. select **Other**
5. click **Browse** → select the FreeBSD ISO
6. check **UEFI Boot** → click Continue
7. set RAM to **4096 MB** (4 GB)
8. set CPU cores to **2**
9. click Continue
10. set storage to **64 GB**
11. click Continue
12. skip shared directory → click Continue
13. name the VM **FreeBSD**
14. click **Save**

---

## 3. install FreeBSD

### boot installer

1. click **Play** to start the VM
2. wait for installer to load
3. select **Install** → press Enter
4. select keyboard layout → press Enter
5. enter hostname (e.g. `freebsd`) → press Enter

### distribution

6. at **Distribution Select**:
   - uncheck all optional components
   - check **lib32** only
   - press Enter

### disk

7. select **vtbd0** disk → press Enter
8. select **Auto (UFS)** partitioning → press Enter
9. select **GPT** partition scheme → press Enter
10. review partition layout → select **Finish** → press Enter
11. select **Commit** to write changes → press Enter
12. wait for installation to complete

### root password

13. enter **root password** (twice)

### network

14. select **vtnet0** for network → press Enter
15. select **Yes** for IPv4 → press Enter
16. select **Yes** for DHCP → press Enter
17. select **No** for IPv6 → press Enter
18. confirm DNS resolver → press Enter

### timezone

19. select your **region** → press Enter
20. select your **country** → press Enter
21. select your **timezone** → press Enter
22. confirm timezone → select **Yes**
23. skip date/time config → press Enter

### services

24. at **System Configuration**:
    - check **sshd** (SSH daemon)
    - press Enter
25. at **System Hardening** → press Enter (defaults fine)

### create user

26. select **Yes** to add a user
27. enter username → press Enter
28. enter full name → press Enter
29. accept default uid → press Enter
30. accept default login group → press Enter
31. enter **wheel** for additional groups → press Enter
32. accept default login class → press Enter
33. accept default shell → press Enter
34. accept default home directory → press Enter
35. use password auth → **Yes**
36. enter user password (twice)
37. lock account → **No**
38. confirm user details → **Yes**
39. add another user → **No**

### finish

40. select **Exit** → press Enter
41. select **No** to manual config
42. select **Reboot**

---

## 4. eject ISO

1. after reboot, stop the VM
2. right-click VM → **Edit**
3. go to **Devices** → **CD/DVD**
4. click **Clear** to remove ISO
5. click **Save**
6. start VM again

---

## 5. first boot

1. VM boots from disk
2. login prompt appears
3. login with your username and password
4. FreeBSD is running

---

## result

- clean FreeBSD install
- UEFI + GPT + UFS
- VirtIO disk + network
- sshd enabled
- next: set up SSH access → see [freebsd-ssh](freebsd-ssh.md)
