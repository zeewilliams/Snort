# 🛡️ Mitigating Attacks by Creating Rules Using Snort

This project demonstrates how to detect and mitigate live attacks using Snort, based on the TryHackMe Snort Challenge – Live Attacks. The challenge involves analyzing network traffic to identify malicious activities and crafting custom Snort rules to prevent them.

## 🔧 Tools & Technologies

- Snort
- Wireshark
- TryHackMe Platform

## 📚 Scenarios Covered

### Scenario 1: Brute-Force Attack

- **Objective**: Detect and block SSH brute-force attempts.
- **Approach**:
  - Ran Snort in sniffer mode to capture traffic.
  - Identified repeated SSH login attempts from a specific IP.
  - Created a custom Snort rule to alert on multiple failed SSH login attempts.
  - Switched Snort to IPS mode to block the malicious IP.

![Brute-Force Detection](images/scenario1-brute-force.png)

### Scenario 2: Reverse Shell Attack

- **Objective**: Detect and block reverse shell connections.
- **Approach**:
  - Monitored outbound traffic for unusual connections.
  - Detected traffic on port 4444, commonly used for reverse shells.
  - Crafted a Snort rule to alert on outbound connections to port 4444.
  - Implemented the rule in IPS mode to prevent the reverse shell.

![Reverse Shell Detection](images/scenario2-reverse-shell.png)

## 📁 Project Structure

- `rules/local.rules`: Custom Snort rules for detecting specific attack patterns.
- `logs/`: Contains Snort log files generated during analysis.
- `images/`: Screenshots illustrating detection and mitigation steps.
- `walkthrough/THM-Snort-Challenge-Walkthrough.md`: Detailed walkthrough of the challenge and solutions.

## 📖 References

- [TryHackMe: Snort Challenge – Live Attacks](https://tryhackme.com/room/snortchallenges2)
- [Jasper Alblas' Walkthrough](https://www.jalblas.com/blog/thm-snort-challenge-live-attacks-walkthrough/)
```

---

## 🖼️ Images

Ensure you include relevant screenshots in the `images/` directory:

* `scenario1-brute-force.png`: Screenshot showing Snort alerting on SSH brute-force attempts.
* `scenario2-reverse-shell.png`: Screenshot displaying detection of reverse shell activity.

---

## 🛠️ Snort Rules (`rules/local.rules`)

```snort
# Rule to detect SSH brute-force attempts
alert tcp any any -> any 22 (msg:"SSH Brute-Force Attempt"; flags:S; threshold:type threshold, track by_src, count 5, seconds 60; sid:1000001; rev:1;)

# Rule to detect reverse shell connections on port 4444
alert tcp any any -> any 4444 (msg:"Potential Reverse Shell Detected"; sid:1000002; rev:1;)
```

---

## 📄 Walkthrough

Create a detailed walkthrough in `walkthrough/THM-Snort-Challenge-Walkthrough.md` outlining:

* Steps taken to identify each attack.
* Commands used to run Snort in different modes.
* Analysis of captured traffic.
* Creation and testing of custom rules.
* Transition from detection to prevention.
