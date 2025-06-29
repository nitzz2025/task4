## Task 4: Setup and Use a Firewall on Linux with UFW
# Objectives
The objective for this activity is to establish and verify some fundamental firewall rules using UFW (Uncomplicated Firewall) on a Linux PC. At the end of this activity, students will be able to:
    • View current firewall settings.
    • Restrict or authorize traffic on select ports.
    • Test their rules on correct facts.
    • Roll back firewall changes to return to the original state.
This exercise makes you more knowledgeable about how Linux firewalls work, helps you learn basic security concepts, and prepares you for securing real-world machines.

🛠️ Used Tools
    • Operating System: Ubuntu Linux (any Debian-based distro)
    • Firewall Tool: UFW (Uncomplicated Firewall)
    • Testing Tools:
        ◦ telnet (testing blocked ports)
        ◦ ssh (to verify allowed ports)
        ◦ netstat, ss, or nmap (optional if scanning ports

Step-by-Step Division of Work:
# Step 1: Enable UFW
Activate the firewall on your Linux PC:
sudo ufw enable
Check its current status:
sudo ufw status verbose
# Step 2: View Current Rules
Display active firewall rules as a numbered list for easy administration:
sudo ufw status numbered
# Step 3: Block inbound traffic on port 23 (telnet)
Port 23 is used by Telnet, and Telnet is insecure and should usually be disabled.
sudo ufw deny 23
# Step 4: Experiment with the Block Rule
Try connecting locally on the blocked port. If the firewall is functioning properly, the connection will be refused or will hang.
telnet localhost 23
You can be asked to install telnet:
sudo apt install telnet
# Step 5: Allow SSH (Port 22)
Ensure SSH (Port 22) is expressly allowed if you are working on a remote system:
sudo ufw allow 22
# Step 6: Delete Block Rule (Clean Up)
First, determine which rule number includes the Telnet block:
sudo ufw status numbered
Then delete it by its rule number:
sudo ufw delete <RULE_NUMBER>
# Step 7: Conclusion – How Firewalls Work
It acts as frontend to iptables and lets you maintain firewall rules easily.
    - Allow rules let some traffic pass through (e.g., sudo ufw allow 80 for web).
    - Deny rules halt traffic (e.g., sudo ufw deny 23).
    - Rules can be for specific ports, IPs, and protocols.
    - Precedence does matter. UFW processes rules top-down.
    - Firewalls play a significant role in preventing undesirable or harmful traffic and serve as a security guard.
# Conclusion
By carrying out this activity, users will:
    - Familiarize themselves with how to use firewall rules on Linux.
    - Learn how to block insecure services (e.g., Telnet).
    - Be able to enable secure services (e.g., SSH).
    - Be able to test and reverse firewall changes.
    - Learn how firewalls secure computer systems from unauthorized access.
