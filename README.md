# Cybersecurity-Incident-Report-Network-Traffic-Analysis


## Part 1: Summary of the Problem Found in the tcpdump Log

As part of the **DNS protocol**, the **UDP protocol** was used to contact the **DNS server** to retrieve the IP address for the domain **yummyrecipesforme.com**. However, the **ICMP protocol** responded with an error message, indicating issues contacting the DNS server. 

- The **UDP message** from the browser to the DNS server is recorded in the **first two lines** of every log event.
- The **ICMP error response** from the DNS server to the browser is recorded in the **third and fourth lines**, displaying the error message:
  > **"udp port 53 unreachable"**

Since **port 53** is associated with **DNS protocol traffic**, this indicates a problem with the **DNS server**.

Further evidence of **DNS resolution failure** is observed through:
- The **plus sign (`+`)** after the **query identification number 35084**, indicating **flags in the UDP message**.
- The **"A?" symbol**, indicating **flags related to DNS protocol operations**.

Due to the **ICMP error response** regarding **port 53**, it is highly likely that the **DNS server is not responding**. This assumption is reinforced by **flags in the outgoing UDP message and domain name retrieval issues**.

---

## Part 2: Analysis of the Data and Possible Causes

### **Incident Timeline:**
- **Time of Incident:** **1:24 p.m. (Today)**
- **Customer Report:** Customers reported receiving the error message:
  > **"destination port unreachable"**  
  when attempting to access **yummyrecipesforme.com**.

### **Incident Investigation:**
The **cybersecurity team** providing IT services to the organization immediately began investigating the issue. **Packet sniffing tests** were conducted using **tcpdump**, revealing that **DNS port 53 was unreachable**.

### **Potential Causes:**
1. **DNS Server is Down**
   - Could be caused by a **Denial of Service (DoS) attack**.
   - Could result from **misconfiguration or server failure**.

2. **Firewall Blocking Traffic to Port 53**
   - A security policy or misconfigured firewall could be **blocking DNS requests**.

### **Next Steps:**
- **Determine if the DNS server is down** or **if traffic to port 53 is being blocked**.
- **Check firewall settings** to ensure DNS traffic is allowed.
- **Investigate potential DoS attacks** targeting the DNS infrastructure.
- **Restore DNS functionality** to allow customers access to the website.

---

This analysis provides insight into **network traffic anomalies**, identifies **potential causes**, and outlines **next steps** for resolution.
