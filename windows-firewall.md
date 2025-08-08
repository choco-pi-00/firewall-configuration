## 🪟 Practical — Windows Firewall

### 1️⃣ Open Windows Firewall Settings
  > Press Windows + R → type:
  > 
  > wf.msc
  >
  > → press Enter.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/17c3bcaa-621c-4db9-88d3-1d327319f2fa" />


(This opens "Windows Defender Firewall with Advanced Security")

Or go to: 
  > Control Panel → System and Security → Windows Defender Firewall → Advanced settings.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/4a761bdf-69f3-4d1f-877a-a67961f071be" />

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5dc00576-a84b-440d-a45c-f480491f31e8" />

---

### 2️⃣ Understanding the Sections
In the left sidebar, you’ll see:

- **Inbound Rules** → Controls traffic coming in to your PC.

- **Outbound Rules** → Controls traffic going out from your PC.

- **Monitoring** → Shows active rules and connections.

---

### 3️⃣ Create a Rule to Allow Traffic
Example: Allow incoming SSH on port 22 (if running an SSH server).

- In Inbound Rules → click New Rule…

- Select Port → Next.

- Select TCP → Specific local ports: 22 → Next.

- Choose Allow the connection → Next.

- Apply to Domain, Private, Public (or choose specific profiles) → Next.

- Name it something like:

  > Allow SSH (Port 22)
  >
Finish.

---

## 4️⃣ Create a Rule to Block Traffic
Example: Block HTTP traffic on port 80.

- In Inbound Rules → New Rule…

- Select Port → Next.

- TCP → Specific local ports: 80.

- Choose Block the connection.

- Apply to needed profiles.

- Name it:

  > Block HTTP (Port 80)
  >

---

## 5️⃣ Test Your Firewall Rule
To check if a port is open/blocked, run in PowerShell:

  > Test-NetConnection -ComputerName 127.0.0.1 -Port 80
- If it says TcpTestSucceeded : False → blocked ✅

- If True → allowed 🚀

---

## 6️⃣ View / Export Rules
To see all rules in PowerShell:

  > netsh advfirewall firewall show rule name=all
Export to a file:

  > netsh advfirewall export "C:\firewall-config.wfw"

---

## 7️⃣ Best Practices in Windows
- Use specific rules (only allow the exact program/port/IP you need).

- Give rules clear names for future reference.

- Keep default inbound policy = Block.

- Periodically review and delete unused rules.

---


