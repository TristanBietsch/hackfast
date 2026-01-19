# FreeBSD SSH Setup

headless SSH setup for FreeBSD VM on macOS.
start VM from terminal, SSH in, no window.

---

## prerequisites

- UTM installed
- FreeBSD VM working (see [[freebsd-install]])
- sshd enabled (`sshd_enable="YES"` in `/etc/rc.conf`)

---

## configure port forwarding

port forwarding requires **Emulated VLAN** mode.

1. stop VM
2. right-click VM → Edit
3. Network → change to **Emulated VLAN**
4. click **Port Forward** → New

| setting       | value     |
| ------------- | --------- |
| protocol      | TCP       |
| guest address | (blank)   |
| guest port    | 22        |
| host address  | 127.0.0.1 |
| host port     | 2222      |

5. save

---

## headless mode (optional)

remove display to prevent VM window appearing.

1. Devices → Display
2. right-click → Delete
3. save

> if using Apple Virtualization backend, display may be required for boot.

---

## shell aliases

add to `~/.zshrc`:

```bash
alias utmctl="/Applications/UTM.app/Contents/MacOS/utmctl"

vm() {
    case "$1" in
        start)
            open -gja UTM
            sleep 1
            utmctl start FreeBSD
            echo "Waiting for SSH..."
            while ! nc -z localhost 2222 2>/dev/null; do sleep 1; done
            echo "Ready."
            ;;
        stop)  utmctl stop FreeBSD ;;
        ssh)   shift; ssh user@localhost -p 2222 "$@" ;;
        *)     echo "Usage: vm {start|stop|ssh}" ;;
    esac
}
```

```bash
source ~/.zshrc
```

---

## usage

```bash
vm start      # launch VM, wait for SSH
vm ssh        # connect
vm ssh "cmd"  # run remote command
vm stop       # shutdown
```

---

## troubleshooting

| problem                    | fix                                              |
| -------------------------- | ------------------------------------------------ |
| connection refused         | wait 10-15s, check `service sshd status`         |
| VM window appears          | remove Display device in settings                |
| utmctl not found           | check alias, verify UTM path                     |
| port forward option hidden | requires Emulated VLAN, not Shared Network       |

---

## reference

| setting      | value                        |
| ------------ | ---------------------------- |
| network mode | Emulated VLAN                |
| host port    | 2222                         |
| guest port   | 22                           |
| SSH command  | `ssh user@localhost -p 2222` |

---

## docs

- https://docs.getutm.app/settings-qemu/devices/network/port-forwarding/
- https://docs.getutm.app/advanced/headless/
