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
A firewall is a security system that controls the flow of incoming and outgoing network traffic based on predetermined rules.

2. Difference between stateful and stateless firewall?
Stateful: Tracks active connections and makes decisions based on the connection state.

Stateless: Evaluates each packet independently, without context of connection.

3. What are inbound and outbound rules?
Inbound rules: Control traffic coming into your device.

Outbound rules: Control traffic leaving your device.

4. How does UFW simplify firewall management?
UFW provides an easy-to-use command-line interface to manage iptables, abstracting complex configurations.

5. Why block port 23 (Telnet)?
Telnet transmits data in plaintext, making it insecure. Blocking port 23 prevents potential unauthorized access.

6. What are common firewall mistakes?
Accidentally blocking essential services (e.g., SSH)

Leaving unused ports open

Not setting a default deny policy

Misconfigured NAT rules

7. How does a firewall improve network security?
It filters out malicious or unauthorized traffic, limiting attack vectors and protecting internal systems.

8. What is NAT in firewalls?
NAT (Network Address Translation) maps private IP addresses to public ones, allowing multiple devices to share a single IP securely.
