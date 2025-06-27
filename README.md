# 🔥 Cybersecurity Task 4: Setup and Use a Firewall on Kali Linux

## 🎯 Objective
Configure basic firewall rules using UFW in Kali Linux to allow/deny traffic and test their effect.

---

## 🛠 Tools
- Kali Linux
- UFW (Uncomplicated Firewall)
- netcat, telnet
- gnome-screenshot / xfce4-screenshooter

---

## ⚙️ Steps

1. **Install UFW**  
   `sudo apt update && sudo apt install ufw -y`

2. **Enable UFW**  
   `sudo ufw enable`

3. **Allow SSH (port 22)**  
   `sudo ufw allow 22`  
   📸 `screenshots/allow-ssh.png`

4. **Deny Telnet (port 23)**  
   `sudo ufw deny 23`  
   📸 `screenshots/deny-port-23.png`

5. **Test with Netcat/Telnet**
   - Terminal 1: `sudo nc -lvp 23`
   - Terminal 2: `telnet localhost 23`
   - Output:  
     ```
     Trying ::1...
     Connection failed: Connection refused
     Trying 127.0.0.1...
     telnet: Unable to connect to remote host: Connection refused
     ```
   📄 `telnet_test_output.txt`  
   📸 `screenshots/deny-port-23-test.png`

6. **Remove Telnet Rule**  
   `sudo ufw delete deny 23`

7. **Check Final Rules**  
   `sudo ufw status verbose`  
   📸 `screenshots/ufw-status.png`

---

❓ Interview Questions & Answers
1. What is a firewall?
A firewall is a security system that monitors and filters incoming and outgoing network traffic based on predefined security rules.

2. What is the difference between stateful and stateless firewalls?
- Stateful firewalls keep track of active connections and use that context to determine if packets are part of an allowed session.
- Stateless firewalls treat each packet individually and don’t retain session information.

3. What are inbound and outbound rules?
- Inbound rules control incoming traffic to your device.
- Outbound rules control traffic leaving your device.

4. How does UFW simplify firewall management?
UFW provides a user-friendly command-line interface to manage `iptables`, making it easier to allow or block traffic without writing complex rules.

5. Why should port 23 (Telnet) be blocked?
Telnet sends data in plaintext and is not encrypted. Blocking port 23 helps prevent unauthorized or insecure access.

6. What are some common firewall mistakes?
- Forgetting to allow SSH and locking yourself out
- Leaving unnecessary ports open
- Misconfigured rule order
- Not setting a default deny policy

7. How does a firewall improve network security?
It controls traffic based on policies, limits exposure to threats, and blocks unauthorized access to services and ports.

8. What is NAT in firewalls?
NAT (Network Address Translation) maps private IP addresses to a public IP address, allowing internal devices to securely access the internet.
