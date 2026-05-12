[redteam-mastery-roadmap.md](https://github.com/user-attachments/files/27655734/redteam-mastery-roadmap.md)
# 12-Month Red Team Mastery Roadmap

> **The Principle:** Every phase builds one layer of the stack — OS internals → network + protocols → web + binary exploitation → full-chain thinking. By month 12, CTF machines are puzzles your logic already knows how to disassemble.

## Phase 1: Foundation — How computers actually work
**Months 1–3** | *Category: Foundation*

### Week 1: Linux internals deep dive — processes & memory
- [ ] Read how the Linux kernel manages processes: fork(), exec(), process trees, /proc filesystem
- [ ] Write C programs that use fork/exec manually
- [ ] Map out: what happens from power-on to a bash prompt?
- [ ] Tool: strace. Run it on every command you use this week.

### Week 2: File system, permissions & privilege model
- [ ] Read the Linux permission model from source level: uid/gid/euid/egid
- [ ] Understand setuid binaries: write one in C, strace it
- [ ] Map the /proc/[pid]/ layout for a running process
- [ ] Exercise: given a setuid binary, think of how it could be abused.

### Week 3: Memory layout — stack, heap, segments
- [ ] Draw the exact virtual memory layout of a running Linux process
- [ ] Write C programs to deliberately read the layout via /proc/self/maps
- [ ] Understand stack pointer and base pointer — draw a stack frame by hand
- [ ] Read how malloc works internally (glibc malloc)

### Week 4: How the CPU executes your code
- [ ] Learn x86-64 calling conventions
- [ ] Disassemble a simple C function with objdump/gdb
- [ ] Understand function prologue/epilogue and WHY
- [ ] Read about CPU rings (0/3)

### Week 5: What happens when your program crashes
- [ ] Generate a segfault deliberately, read core dump with gdb
- [ ] Understand null pointer dereference at the machine level
- [ ] Read about signals: SIGSEGV, SIGBUS, SIGILL
- [ ] Exercise: write a program that reads from address 0x0.

### Week 6: Networking internals — TCP/IP from the kernel's view
- [ ] Read the kernel's socket API: socket() → bind() → listen() → accept()
- [ ] Write a raw TCP server in C from scratch
- [ ] Use Wireshark: capture a TCP handshake, HTTP request, DNS query
- [ ] Understand the kernel's network stack layers

### Week 7: Protocols you must understand cold
- [ ] Read HTTP/1.1 RFC
- [ ] Read how DNS actually resolves
- [ ] Read TLS handshake in detail
- [ ] Write an HTTP server by hand (raw sockets)

### Week 8: Authentication & session mechanics
- [ ] Read how cookies work at the HTTP level
- [ ] Understand JWTs: base64 decode, none-algorithm issue
- [ ] Read how OAuth2 flows work
- [ ] Exercise: what breaks if server never validates JWT signature?

### Week 9: Cryptography intuition (not math — mechanics)
- [ ] Understand symmetric vs asymmetric encryption
- [ ] Read about padding oracle attacks
- [ ] Learn what CBC mode is and bit-flipping
- [ ] Exercise: derive what can be found from a padding error.

### Week 10: Web architecture — from browser to database
- [ ] Map the full web request lifecycle
- [ ] Read how SQL queries actually execute
- [ ] Understand prepared statements at the driver level
- [ ] Exercise: find injection points in a raw SQL query.

### Week 11: How web servers handle input
- [ ] Read how CGI, WSGI, and PHP-FPM work
- [ ] Understand deserialization
- [ ] Read how PHP's unserialize() works
- [ ] Exercise: what can you trigger with controlled serialized data?

### Week 12: Phase 1 consolidation — build your mental model
- [ ] Write: 'what a computer does with a web request'
- [ ] Identify attacker leverage at each layer
- [ ] Identify 3 things you still don't understand
- [ ] Synthesis and writing focus.

---

## Phase 2: Exploitation mechanics from first principles
**Months 4–6** | *Category: Exploit Logic*

### Week 13: Buffer overflows — why memory corruption happens
- [ ] Write a vulnerable C program with gets()
- [ ] Use gdb to watch rip get overwritten
- [ ] Draw the stack to see the 8-byte offset
- [ ] Understand the mechanism of rip control.

### Week 14: Writing your first shellcode — from scratch
- [ ] Write x86-64 shellcode for /bin/sh (no libc)
- [ ] Fix shellcode to be NULL-free
- [ ] Use strace on a shell to see syscalls
- [ ] Exercise: write shellcode to read /etc/passwd.

### Week 15: Stack canaries and ASLR
- [ ] Read how stack canaries are implemented
- [ ] Understand ASLR randomization and relative offsets
- [ ] Read about format string vulnerabilities
- [ ] Exercise: how to leak canary with format string?

### Week 16: ROP — return-oriented programming logic
- [ ] Understand why NX/DEP prevents injection
- [ ] Find gadgets manually with ROPgadget/ropper
- [ ] Understand why control of rsp = control of execution
- [ ] Build a ROP chain manually to call system('/bin/sh')

### Week 17: Heap exploitation fundamentals
- [ ] Read glibc malloc internals (free chunks, bins)
- [ ] Understand use-after-free (UAF) mechanism
- [ ] Read about heap overflow chunk header overwrites
- [ ] Exercise: what to overwrite with a UAF bug?

### Week 18: SQL injection — derive the attack from the query
- [ ] Find injection points by reading query structure
- [ ] Understand UNION SELECT requirements
- [ ] Derive error, blind, and time-based injection
- [ ] Exercise: minimum requests for blind SQLi?

### Week 19: XSS — understand the browser security model
- [ ] Read the Same-Origin Policy (SOP)
- [ ] Understand what JS in a victim's origin unlocks
- [ ] Read CSP (Content Security Policy) and bypasses
- [ ] Exercise: execute JS with script-src 'self'.

### Week 20: Command injection & SSRF logic
- [ ] Read shell command parsing characters
- [ ] Understand when system() or popen() are used
- [ ] Read SSRF and internal service reach
- [ ] Exercise: SSRF on AWS? Reason the URL.

### Week 21: File inclusion & path traversal
- [ ] Read how PHP include/require works
- [ ] Understand why ../../../etc/passwd works
- [ ] Read LFI to RCE paths (log poisoning, etc.)
- [ ] Exercise: think through RCE paths from LFI.

### Week 22: Authentication bypass logic
- [ ] Read IDOR (Insecure Direct Object Reference)
- [ ] Understand PHP type juggling logic
- [ ] Study JWT attacks (alg:none, key confusion)
- [ ] Exercise: list categories of bypasses for a login form.

### Week 23: Privilege escalation — Linux
- [ ] Read sudo misconfigurations
- [ ] Understand SUID binary abuse
- [ ] Read about capabilities (CAP_NET_RAW, etc.)
- [ ] Exercise: build a mental checklist for privesc.

### Week 24: Active Directory — architecture before attacks
- [ ] Read AD protocols (Kerberos, LDAP, SMB)
- [ ] Draw the Kerberos flow from memory
- [ ] Read about TGT, service tickets, and the KDC
- [ ] Understand architecture first.

### Week 25: AD attacks — derive them from the protocol
- [ ] Kerberoasting: derive from ticket encryption
- [ ] AS-REP roasting: derive from preauth requirements
- [ ] Pass-the-hash: derive from NTLM validation
- [ ] Exercise: list escalation paths for a low-priv user.

### Week 26: Phase 2 consolidation — connect the layers
- [ ] Write attack decision tree for web apps
- [ ] Write privilege escalation tree for Linux
- [ ] Write escalation order for Windows AD
- [ ] Identify and fill gaps.

---

## Phase 3: Full chain thinking & chaining vulns
**Months 7–9** | *Category: Chain Building*

### Week 27: Reconnaissance logic — what to look for and why
- [ ] Build mental model of exposed information
- [ ] Read what technologies leak about themselves
- [ ] Understand behavioral fingerprinting
- [ ] Exercise: map a public web app's surface.

### Week 28: Source code auditing — reading code as an attacker
- [ ] Learn sources vs sinks in PHP, Python, Node.js
- [ ] Practice finding vulns in code before reading CVEs
- [ ] Identify grep patterns for auditing
- [ ] Exercise: audit a small open-source app.

### Week 29: Building chains: foothold → privilege escalation
- [ ] Document every decision in a full-chain scenario
- [ ] Write chains as decision trees
- [ ] Practice pivoting across interfaces
- [ ] Focus on the WHY at every step.

### Week 30: Windows exploitation fundamentals
- [ ] Read Windows process model (ACLs, tokens)
- [ ] Understand unquoted service paths, DLL hijacking
- [ ] Read about SeImpersonatePrivilege
- [ ] Exercise: derive unquoted service path exploit.

### Week 31: Post-exploitation thinking
- [ ] Read credential storage on Linux
- [ ] Read credential storage on Windows (LSASS, SAM)
- [ ] Understand lateral movement and detection
- [ ] Build persistence establishment checklist.

### Week 32: Evasion logic — understand defenses to bypass them
- [ ] Read how AV signatures work
- [ ] Understand obfuscation (XOR, etc.)
- [ ] Read EDR behavior and syscall hooking
- [ ] Exercise: execute payload without touching disk.

### Week 33: Network pivoting & tunneling
- [ ] Read SSH port forwarding (Local, Remote, Dynamic)
- [ ] Understand SOCKS proxies and proxychains
- [ ] Read chisel/ligolo-ng internals
- [ ] Exercise: pivot to reach machine B via machine A.

### Week 34: Cloud attack surface — AWS fundamentals
- [ ] Read AWS IAM model (roles, policies)
- [ ] Understand EC2 metadata service (169.254.169.254)
- [ ] Read S3 bucket misconfigurations
- [ ] Exercise: SSRF to AWS privesc.

### Week 35: Race conditions & logic flaws
- [ ] Read TOCTOU race conditions
- [ ] Understand web race conditions
- [ ] Read about business logic flaws
- [ ] Exercise: design a flow with both flaws.

### Week 36: Protocol-level attacks
- [ ] Read DNS rebinding vs SOP
- [ ] Understand WebSocket security
- [ ] Read HTTP request smuggling (CL vs TE)
- [ ] Exercise: derive smuggling from header disagreement.

### Week 37: Full machine simulation — web → foothold → root
- [ ] Solve a retired HTB machine (no walkthroughs)
- [ ] Document every decision and failure
- [ ] Compare path to the intended path
- [ ] Identify decision-making gaps.

### Week 38: Full machine simulation — AD focused
- [ ] Solve an AD-focused HTB machine
- [ ] Justify every enumeration decision
- [ ] Map the full kill chain
- [ ] Fill gaps in tool understanding.

### Week 39: Phase 3 consolidation — attack methodology formalization
- [ ] Write personal attack methodology doc (3+ pages)
- [ ] Write category-specific starting questions
- [ ] Identify weakest areas
- [ ] Write step-by-step approach for new targets.

---

## Phase 4: Speed, gaps & real-world readiness
**Months 10–12** | *Category: Mastery*

### Week 40: Timed simulation — 4 hours, no hints
- [ ] Solve a Medium/Hard machine in 4 hours
- [ ] Track time for recon and rabbit holes
- [ ] Identify first-check misses
- [ ] Stress-test logic under pressure.

### Week 41: Revisit and break your own tools
- [ ] Modify targets to break your exploits
- [ ] Change shellcode for different bad-chars
- [ ] Rewrite ROP chains for modified binaries
- [ ] Demonstrate understanding over memory.

### Week 42: Custom tooling — write what you need
- [ ] Write Python port scanner (raw sockets)
- [ ] Write directory bruter with rate limiting
- [ ] Write blind SQLi automated tester
- [ ] Goal: don't use tools, write them.

### Week 43: Deepen your weakest area (week 1)
- [ ] Gap analysis: focus on weakness #1
- [ ] Read documentation, not tutorials
- [ ] Write PoC exploit from scratch
- [ ] e.g., manual Kerberoasting.

### Week 44: Deepen your weakest area (week 2)
- [ ] Focus on weakness #2
- [ ] Read patches for related CVEs
- [ ] Teach the vulnerability to test understanding
- [ ] Teaching-quality explanation focus.

### Week 45: Deepen your weakest area (week 3)
- [ ] Focus on weakness #3
- [ ] Map HackerOne reports to your mental model
- [ ] Update attack methodology doc
- [ ] Refine decision tree.

### Week 46: Binary exploitation — return to rop & heap
- [ ] Implement tcache poisoning manually
- [ ] Read about one-gadgets
- [ ] Understand ret2libc with ASLR/leaks
- [ ] Exercise: exploit binary with all protections.

### Week 47: Web — advanced techniques
- [ ] Read prototype pollution
- [ ] Understand template injection (SSTI)
- [ ] Read OAuth misconfigurations
- [ ] Exercise: enumerate OAuth assumptions.

### Week 48: Full simulation — 2 machines, 8 hours
- [ ] Simulate a CTF day (8 hours, 2 boxes)
- [ ] Write mini after-action report
- [ ] Identify 'tool-dependency' gaps
- [ ] Fill gaps before week 52.

### Week 49: Networking attacks & packet manipulation
- [ ] Read ARP spoofing protocol details
- [ ] Write Python ARP poisoner with Scapy
- [ ] Read VLAN hopping (802.1Q)
- [ ] Exercise: reason about L2 attacks.

### Week 50: Advanced AD — DCSync, Golden/Diamond Tickets
- [ ] Read DCSync and replication rights
- [ ] Understand Golden Ticket forgery requirements
- [ ] Read Diamond Ticket vs Golden Ticket
- [ ] Exercise: describe TGT craft (ASN.1 structure).

### Week 51: Report writing — think like a professional
- [ ] Write professional vuln reports for past exploits
- [ ] Focus on impact and remediation for devs
- [ ] Skill synthesis: knowledge to output
- [ ] Update Phase 1 methodology doc.

### Week 52: Final validation — Hard machine, no help
- [ ] Solve a Hard HTB machine, no hints
- [ ] Predict results before running tools
- [ ] Compare expectation to reality
- [ ] Final logic gap check.

---

