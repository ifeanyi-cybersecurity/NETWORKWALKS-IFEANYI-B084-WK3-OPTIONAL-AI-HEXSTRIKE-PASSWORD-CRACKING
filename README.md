# NETWORKWALKS-IFEANYI-B084-WK3-OPTIONAL-AI-HEXSTRIKE-PASSWORD-CRACKING

**Networkwalks Cybersecurity Internship — Batch B084**
**Intern:** Nnani Ifeanyi
**Week 3 — Optional Module: AI-Assisted Password Cracking**

## Task

Crack the password of `hash3.networkwalks_flag1.pdf` using John the Ripper,
with Claude Desktop (AI) driving the attack through a HexStrike-AI MCP server
running on Kali Linux — instead of running JTR commands by hand.

## Environment

- Kali Linux VM
- [HexStrike-AI](https://github.com/0x4m4/hexstrike-ai) MCP server + MCP bridge (`hexstrike_server.py` + `hexstrike_mcp.py`)
- Claude Desktop, connected to HexStrike over MCP
- Wordlist: `rockyou.txt` (`/usr/share/wordlists`, pre-installed on Kali)

## Steps performed

**1. Installed and started the HexStrike-AI MCP server** and bridge on Kali.

![HexStrike-AI installation](screenshots/Hexstrike-installation.png)
![HexStrike-AI server running](screenshots/Hexstrike-running.png)

**2. Confirmed the bridge was healthy.**

![Health check confirming the HexStrike server is reachable](screenshots/Health-check.png)

**3. Registered the MCP connector in Claude Desktop's config.**

![MCP server configuration in Claude Desktop](screenshots/MCP-server-conf.png)
![HexStrike-Claude MCP bridge connected](screenshots/Hexstrike-Claude-Bridge.png)

**4. Confirmed John the Ripper was reachable through HexStrike**, then copied
the target PDF to the Kali Desktop and prompted Claude to calculate the
hash and run John the Ripper against it with `rockyou.txt`.

![Confirming JTR is available through HexStrike](screenshots/JTR-confirmation.png)

**5. Claude called the HexStrike tools** to extract the hash and run
`john --format=PDF --wordlist=/tmp/rockyou.txt /tmp/pdf_hash.txt`. John the
Ripper cracked the password: **`password1`**

![AI-driven crack result](screenshots/AI-file-cracked.png)

**6. Opened the PDF** on the Kali Desktop with the recovered password to
confirm it unlocked — "Congratulations! You have captured another flag."

![PDF unlocked with the cracked password](screenshots/Cracked.png)

## Demo video

[`WK3-OPTIONAL-AI-crack-highlight.mp4`](WK3-OPTIONAL-AI-crack-highlight.mp4) —
a short highlight clip starting a few seconds before John the Ripper's result
appears, through the password being used to open the file and the flag being
captured. (Full raw recording is several minutes long and mostly shows the
wordlist attack running; this cut keeps just the payoff for the write-up.)

## Key takeaway

The cracking step itself is unchanged — it's still John the Ripper and
`rockyou.txt` doing the work. What HexStrike + Claude changes is the
*interface*: instead of typing the `john` command, the operator describes the
goal in plain English and the AI selects and runs the right tool through the
MCP server, then reports the result back in the chat. Useful for speeding up
repetitive recon/cracking workflows, but the underlying security lesson is
identical to WK3-PM1: a short, common password falls to a dictionary attack
in seconds either way.

---
*Part of the Networkwalks Cybersecurity Internship — Batch B084.*
*Lab files and target PDFs provided by Networkwalks for training purposes only.*
