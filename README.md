#  Task 4: Setup and Use a Firewall on Linux with UFW

##  Objective

The goal of this task is to **configure and test basic firewall rules** using `UFW` (Uncomplicated Firewall) on a Linux machine. By the end of this task, users will understand how to:
- View current firewall settings.
- Block or allow traffic on specific ports.
- Test their rules for correctness.
- Revert firewall changes to restore the original system state.

This task improves your understanding of how Linux firewalls work, helps you grasp basic security principles, and prepares you for securing real-world systems.

---

## 🛠️ Tools Used

- **Operating System**: Ubuntu Linux (or any Debian-based distro)
- **Firewall Tool**: UFW (Uncomplicated Firewall)
- **Testing Tools**: 
  - `telnet` (to test blocked ports)
  - `ssh` (to validate allowed ports)
  - `netstat`, `ss`, or `nmap` (optional for port checking)

---

##  Task Breakdown: Step-by-Step

###   Step 1: Enable UFW

Activate the firewall on your Linux machine:

```
sudo ufw enable
```

Check its current status:
```
sudo ufw status verbose
```

###   Step 2: View Current Rules
Display existing firewall rules in a numbered list for easier management:

```
sudo ufw status numbered
```

###   Step 3: Block Inbound Traffic on Port 23 (Telnet)
Port 23 is used by Telnet, which is insecure and should typically be blocked.
```
sudo ufw deny 23
```

###   Step 4: Test the Block Rule
Try connecting to the blocked port locally. If the firewall is working correctly, the connection should be refused or hang.
```
telnet localhost 23
```

You may need to install telnet:
```
sudo apt install telnet
```
#### Step 5: Allow SSH (Port 22)
Ensure that SSH (Port 22) is explicitly allowed, especially important if you're working on a remote system:
```
sudo ufw allow 22
```
### Step 6: Remove the Block Rule (Clean Up)
First, check which rule number corresponds to the Telnet block:
```
sudo ufw status numbered
```
Then delete it using its rule number:
```
sudo ufw delete <RULE_NUMBER>
```
### Step 7: Summary – How Firewalls Work

UFW acts as a frontend for iptables, allowing you to manage firewall rules easily.

-Allow rules let specific traffic through (e.g., sudo ufw allow 80 for web).

-Deny rules block traffic (e.g., sudo ufw deny 23).

-Rules can apply to specific ports, IPs, and protocols.

-Order matters. UFW processes rules top-down.

-Firewalls are critical in filtering unwanted or dangerous traffic, acting as a security gatekeeper.
