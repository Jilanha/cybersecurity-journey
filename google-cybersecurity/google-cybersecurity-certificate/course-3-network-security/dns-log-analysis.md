# Packet Analysis: DNS Requests & ICMP Port Unreachable  
🗓️ Completed: July 21, 2025

---

## 🧠 Objective:
Review and interpret a short packet log to understand repeated DNS requests and the ICMP responses that followed. Apply analyst-level thinking to extract behavioral patterns, not just packet content.

---

## 📄 Packet Snippet Analyzed:
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 254

13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 320

13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 150

---

## 🔍 What I Observed:

- All 3 DNS requests ask for the **same domain**: `yummyrecipesforme.com`
- All 3 target the **same DNS server IP**: `203.0.113.2`
- All attempts are met with an ICMP “port unreachable” — indicating **UDP port 53 is closed or blocked**
- The requests are spaced **exactly 2 minutes apart**, suggesting **automation or a persistent background process**

---

## 🧠 My Takeaways:

- **Timestamps matter** — I learned not to ignore them. Repetition on a strict schedule is a signal of **non-human activity**.
- **ICMP port unreachable** responses reveal failed DNS resolution, which may be due to:
  - A misconfigured DNS server
  - A firewall or routing issue
  - A possible **malware callback to a dead domain**
- 3 requests alone may not be suspicious, but **when the timing, response, and behavior are all consistent**, it's worth flagging.

---

## 🛠️ Analyst Mindset Lessons:

- Never assume something is benign just because it’s repeated — context (like time) reveals intent.
- Look beyond the literal packet — **how often, to whom, and what the behavior means** is often more important.
- Even a small log can offer a **story** if you read between the lines.

---

## 🔗 Tools Not Used Yet (but coming soon):
- Wireshark (for visual breakdown)
- tcpdump (command line capture & filter)
- Threat Intel (domain reputation checks)

---

## ✅ Status:
This entry marks a turning point in how I view logs — not just reading them, but **interpreting their behavior**.

