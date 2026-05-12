import markdown

# Data for the C Hacking Roadmap
c_phases = [
    {
        "title": "Phase 1: Deep C Fundamentals",
        "sub": "Duration: 1.5 Months",
        "badge": "Core Logic",
        "topics": ["Advanced Pointers & Memory", "Structs, Unions & Bitfields", "The Compilation Toolchain", "Manual Memory Management"],
        "projects": ["Custom Memory Allocator (malloc/free)", "Memory-safe String Library"]
    },
    {
        "title": "Phase 2: Linux System Programming",
        "sub": "Duration: 2 Months",
        "badge": "System Level",
        "topics": ["Syscalls & The Kernel API", "Process Lifecycle (fork/exec)", "Inter-Process Communication", "Socket Programming (Raw Sockets)"],
        "projects": ["Multi-threaded Web Server", "Raw Socket Packet Sniffer"]
    },
    {
        "title": "Phase 3: The Hacker's C (Security)",
        "sub": "Duration: 2.5 Months",
        "badge": "Exploitation",
        "topics": ["x86_64 Assembly Fundamentals", "Binary Analysis & Reverse Engineering", "Memory Corruption Mechanics", "GDB & Ghidra Mastery"],
        "projects": ["CrackMe Challenge Set", "Custom Buffer Overflow Exploit Lab"]
    }
]

def generate_markdown(phases, filename):
    md_content = "# C for Hacking: Professional Learning Roadmap\n\n"
    md_content += "> **Focus:** Mastering memory, system internals, and exploitation logic through pure C.\n\n"
    
    # Adding Mermaid Flowchart for GitHub rendering
    md_content += "### 🗺️ Visual Path\n"
    md_content += "```mermaid\ngraph LR\n"
    md_content += "    A[Phase 1: Deep C] --> B[Phase 2: System Programming]\n    B --> C[Phase 3: Exploitation Logic]\n\n"
    md_content += "    style A fill:#7c4dff,stroke:#fff,stroke-width:2px,color:#fff\n"
    md_content += "    style B fill:#00c853,stroke:#fff,stroke-width:2px,color:#fff\n"
    md_content += "    style C fill:#ff6d00,stroke:#fff,stroke-width:2px,color:#fff\n"
    md_content += "```\n\n---\n\n"

    for p in phases:
        md_content += f"## {p['title']}\n"
        md_content += f"**{p['sub']}** | `{p['badge']}`\n\n"
        
        md_content += "### 🧠 Mastery Topics\n"
        for topic in p['topics']:
            md_content += f"- [ ] {topic}\n"
        
        md_content += "\n### 🛠️ Phase Projects\n"
        for proj in p['projects']:
            md_content += f"- `PROJ:` {proj}\n"
        md_content += "\n---\n\n"

    with open(filename, 'w', encoding='utf-8') as f:
        f.write(md_content)
    print(f"File '{filename}' generated successfully.")

# Execute
generate_markdown(c_phases, 'c-hacking-roadmap.md')
