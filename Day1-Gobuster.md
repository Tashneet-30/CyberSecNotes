# Cyber Security Learnings – Day 1 (03 March 2025)

## Understanding Gobuster for Web Directory Enumeration

### What is Gobuster?

Gobuster is a command-line tool for finding hidden directories and files on a website. It works by brute-forcing URLs using a predefined wordlist. This is useful in penetration testing to discover unlisted web pages containing sensitive information.

## Using Gobuster in TryHackMe Lab

Today, I worked on a TryHackMe lab with a fake bank website. I used Gobuster to discover hidden pages.
### Command Used:

```bash
gobuster dir -u http://fakebank.thm -w wordlist.txt
```

## Gobuster and Wordlists in Parrot OS

### Breaking Down the Command

| Command Part | Meaning |
|-------------|---------|
| `gobuster dir` | Specifies we are searching for directories |
| `-u http://fakebank.thm` | The target website URL |
| `-w wordlist.txt` | The wordlist file used for guessing directories |

## Does Gobuster Work Without a Wordlist?
❌ **No**, Gobuster does not guess directories randomly. It requires a wordlist to function. If no wordlist is provided, it returns an error.

## What Happens If Wordlist is Missing or Empty?

If `wordlist.txt` does not exist, Gobuster returns the following error:

```bash
Error: stat wordlist.txt: no such file or directory
```


If the wordlist is empty, Gobuster runs but finds nothing.

## Where to Find Prebuilt Wordlists in Parrot OS?

Parrot OS comes with several built-in wordlists, stored in `/usr/share/wordlists/`.

### Useful Wordlists in Parrot OS:

| Wordlist Path | Purpose |
|--------------|---------|
| `/usr/share/wordlists/dirb/common.txt` | Common directory names (good for Gobuster) |
| `/usr/share/wordlists/dirb/big.txt` | Extended version of `common.txt` |
| `/usr/share/wordlists/seclists/Discovery/Web-Content/common.txt` | Another good wordlist for web directory brute force |
| `/usr/share/wordlists/wfuzz/general/common.txt` | Used for fuzzing web applications |

## Using Prebuilt Wordlists in Gobuster

If `wordlist.txt` is missing, use a system wordlist:

```bash
gobuster dir -u http://fakebank.thm -w /usr/share/wordlists/dirb/common.txt
```

## Working with rockyou.txt (Password Wordlist)

`rockyou.txt` is a famous password list, but it is compressed by default.

### Extracting and Using rockyou.txt

```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

Now, you can use it for password attacks with Hydra:

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt http://fakebank.thm/login.php
```

## Key Takeaways from Today’s Learning

✅ Gobuster requires a wordlist; it does not guess randomly.  
✅ If a wordlist is missing or empty, Gobuster fails or finds nothing.  
✅ Parrot OS includes prebuilt wordlists in `/usr/share/wordlists/`.  
✅ `rockyou.txt` is a password wordlist, but it must be extracted before use.  




DAY 02 
# 🛡️ Cyber Security Learnings – Day 2 (21 March 2025)

## 🔍 Understanding Defensive Security  

Defensive security focuses on **preventing cyber attacks** and **detecting intrusions** if they happen.  

🔹 **Red Team** (Attackers) = Offensive Security (Hacking)  
🔹 **Blue Team** (Defenders) = Defensive Security (Protection)  

### 🎯 Goals of Defensive Security  
1. **Prevent intrusions** – Stop hackers from getting in.  
2. **Detect intrusions** – If hackers get in, find them quickly and stop them.  

## 🏰 Key Tasks in Defensive Security  

### 1️⃣ User Cyber Security Awareness  
👨‍💻 **Example**: Training employees to recognize phishing emails and avoid clicking malicious links.  

### 2️⃣ Documenting and Managing Assets  
🖥️ **Example**: Keeping an inventory of company devices to ensure everything is protected.  

### 3️⃣ Updating and Patching Systems  
🔄 **Example**: Regularly updating Windows and security software to fix vulnerabilities.  

### 4️⃣ Setting Up Preventative Security Devices  
🛑 **Firewalls** – Control which traffic enters or leaves the network.  
🛡️ **Intrusion Prevention Systems (IPS)** – Block attacks based on known threats.  
🔍 **Example**: A firewall blocking access to dangerous websites.  

### 5️⃣ Logging and Monitoring for Threats  
👀 **Example**: A company monitoring network traffic to detect unusual activity.  

---

## 🔎 Related Topics in Defensive Security  

### 🔹 Security Operations Center (SOC)  
👮 **What it does**: A team that monitors security threats 24/7.  
🏢 **Example**: Google has a SOC that watches for cyber threats in real-time.  

### 🔹 Threat Intelligence  
🔍 **What it does**: Analyzes hacker techniques to predict future attacks.  
📌 **Example**: Learning from past ransomware attacks to improve security.  

### 🔹 Digital Forensics and Incident Response (DFIR)  
🕵️ **What it does**: Investigates cyber crimes and traces hacker activities.  
🔬 **Example**: Investigating a data breach caused by a stolen password.  

### 🔹 Malware Analysis  
💀 **What it does**: Studies malware to understand how it works and how to stop it.  
🐛 **Example**: Analyzing a suspicious email attachment for hidden viruses.  

---

## ✅ Key Takeaways  
✔️ Defensive security **prevents and detects** cyber attacks.  
✔️ Firewalls, IPS, and monitoring tools help **protect networks**.  
✔️ Blue teams work in **SOC centers** to keep organizations safe.  
✔️ Threat intelligence, DFIR, and malware analysis help in **investigating cyber threats**.  

🔒 **Stay Safe, Stay Secure!** 🛡️  


