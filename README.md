# 🛡️ Mitigating Attacks with Snort – IDS Challenge Lab

![null](THM-CLI.webp) <!-- Replace with a better cover image if available -->

---

## 📘 Introduction

This project showcases the deployment of Snort, a powerful open-source intrusion detection system (IDS), in a simulated lab environment. The challenge is based on TryHackMe’s Snort Challenge, where live attacks are detected and mitigated using custom rules. This exercise strengthens foundational Blue Team skills in traffic analysis, signature-based detection, and response.

---

## 🎯 Objectives

* Set up and configure Snort in a virtual environment
* Analyze malicious traffic patterns using `tcpdump` and `pcap` files
* Write Snort rules to detect and respond to attacks
* Test and validate rule effectiveness with simulated threats

---

## 🧰 Tools & Technologies

| Tool/Service | Purpose                     |
| ------------ | --------------------------- |
| Snort        | Intrusion detection system  |
| Wireshark    | Packet analysis             |
| TryHackMe    | Snort Challenge environment |
| Ubuntu VM    | Host for IDS deployment     |

---

## 🧪 Lab Setup

### ✅ Step 1: Access the TryHackMe Room

1. Navigate to the [Snort Challenge - Live Attacks](https://tryhackme.com/room/snortchallenge) on TryHackMe.
2. Deploy the attack and target machines.

---

### ✅ Step 2: Install Snort

```bash
sudo apt update
sudo apt install snort
```

* Configure the interface and HOME\_NET settings in `/etc/snort/snort.conf`.

---

### ✅ Step 3: Analyze Malicious Traffic

Use tools like Wireshark or tcpdump to inspect traffic:

```bash
tcpdump -i eth0 -nn
```

Identify suspicious patterns such as excessive HTTP requests or scanning behavior.

---

### ✅ Step 4: Write and Test Snort Rules

Example rule to detect Nmap scans:

```bash
alert tcp any any -> any any (msg:"Nmap Scan Detected"; flags:S; threshold:type threshold, track by_src, count 5, seconds 60; sid:1000001;)
```

* Save rule in local.rules and restart Snort:

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

---

### ✅ Step 5: Mitigate via Alerts or RESP

Extend rules to block or log based on specific attack signatures (e.g., web shell upload or RFI detection).

---

## 📸 Screenshots

| Description                  | Screenshot                        |
| ---------------------------- | --------------------------------- |
| Snort detecting Nmap scan    | ![Scan Detected](snort-nmap.png)  |
| Custom Snort rule match      | ![Rule Match](snort-rule.png)     |
| Traffic capture in Wireshark | ![Traffic Capture](wireshark.png) |

---

## ✅ Key Takeaways

* ✅ Learned how to configure and deploy Snort IDS
* ✅ Practiced writing effective Snort rules
* ✅ Detected and analyzed live attack patterns
* ✅ Strengthened Blue Team incident response skills

---

## 📎 References

* [TryHackMe Snort Challenge Walkthrough](https://www.jalblas.com/blog/thm-snort-challenge-live-attacks-walkthrough/)
* [Snort Documentation](https://www.snort.org/documents)

---

## 📬 About Me

👋 I'm **Zee**, a cybersecurity enthusiast focused on defensive security, incident response, and simulating real-world threats. This lab deepened my hands-on knowledge of intrusion detection and packet analysis using Snort.
