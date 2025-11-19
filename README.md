# Firewall Configuration and Traffic Filtering on Linux using UFW

## Project Overview

This repository contains a small lab (Task 4) that demonstrates how to configure and use the Uncomplicated Firewall (`ufw`) on Debian/Ubuntu-like systems (Kali Linux used in the lab) to filter network traffic and protect a host by allowing or denying specific ports and services.

## Contents

- `commands_used.txt` — list of UFW commands used during the lab.
- `screenshots/` — screenshots captured while performing the lab steps.

## Objectives

- Install and enable UFW.
- List and manage firewall rules.
- Allow and deny specific ports/services.
- Remove rules and verify the firewall status.

## Prerequisites

- A Debian/Ubuntu-based system (Kali Linux was used in the lab).
- User with `sudo` privileges.
- Internet connectivity to install packages if `ufw` is not present.

## Installing UFW (if needed)

On Debian/Ubuntu (run as root or with `sudo`):

```bash
sudo apt update
sudo apt install ufw -y
```

## Quick UFW Usage Summary

Below are the core UFW commands and the sequence used during this lab. These commands are also preserved in `commands_used.txt`.

1. Enable UFW

```bash
sudo ufw enable
```

2. Check existing firewall rules (numbered)

```bash
sudo ufw status numbered
```

3. Block inbound traffic on port 23 (Telnet)

```bash
sudo ufw deny 23
```

4. Allow SSH on port 22

```bash
sudo ufw allow 22
```

5. Delete rule for port 23 (removing deny)

```bash
sudo ufw delete 1
```

6. Verify updated rules

```bash
sudo ufw status numbered
```

7. Disable firewall (Optional)

```bash
sudo ufw disable
```

## Explanation and Notes

- `sudo ufw enable` activates the firewall and applies configured rules.
- `status numbered` is useful when you want to delete a rule by its index (use `sudo ufw delete <num>`).
- Use `allow` to permit traffic to a given port or service, and `deny` to block it.
- Consider allowing only specific IP addresses when exposing services publicly, e.g.:

```bash
sudo ufw allow from 203.0.113.5 to any port 22 proto tcp
```

- Use `ufw limit` to mitigate brute-force attacks on services such as SSH:

```bash
sudo ufw limit ssh
```

## Testing & Verification

- After adding rules, confirm expected behavior by attempting to connect from another host (SSH/Telnet/etc.).
- Check `sudo ufw status verbose` for richer output, including default policies.

## Screenshots

Open the `screenshots/` directory to view lab screenshots that show enabling UFW and the status output.

## Author

Prepared by: girikrishnajetti

## Suggested next steps (commit)

After reviewing the README, you can add and commit it with:

```bash
git add README.md
git commit -m "Add README for Task4: UFW firewall lab"
git push
```

## References

- `ufw` manual: `man ufw`
- Ubuntu UFW documentation: https://help.ubuntu.com/community/UFW
