# 🛡️ NMAP HELIOS
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" width="512" height="512">
  <defs>
    <linearGradient id="bg-grad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#0b0d14" />
      <stop offset="100%" stop-color="#0f1219" />
    </linearGradient>

    <filter id="helios-blue-glow" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="8" result="blur" />
      <feMerge>
        <feMergeNode in="blur" />
        <feMergeNode in="SourceGraphic" />
      </feMerge>
    </filter>
    
    <linearGradient id="cyber-sun-gradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#22d3ee" /> <stop offset="60%" stop-color="#3b82f6" /> <stop offset="100%" stop-color="#1d4ed8" /> </linearGradient>
  </defs>

  <rect width="512" height="512" rx="32" fill="url(#bg-grad)" />

  <polygon points="256,30 460,140 460,372 256,482 52,372 52,140" 
           fill="none" 
           stroke="#22d3ee" 
           stroke-width="4" 
           stroke-opacity="0.2" />

  <polygon points="256,55 432,155 432,357 256,457 80,357 80,155" 
           fill="none" 
           stroke="url(#cyber-sun-gradient)" 
           stroke-width="8" 
           stroke-dasharray="24 16" />

  <g stroke="#3b82f6" stroke-width="4" opacity="0.5">
    <line x1="256" y1="80" x2="256" y2="432" stroke-dasharray="10 10" />
    <line x1="80" y1="256" x2="432" y2="256" stroke-dasharray="10 10" />
    <line x1="130" y1="130" x2="382" y2="382" stroke="#22d3ee" opacity="0.25" />
    <line x1="130" y1="382" x2="382" y2="130" stroke="#22d3ee" opacity="0.25" />
  </g>

  <circle cx="256" cy="256" r="140" fill="none" stroke="#1d4ed8" stroke-width="4" opacity="0.4" />
  <circle cx="256" cy="256" r="100" fill="none" stroke="#22d3ee" stroke-width="6" stroke-dasharray="64 32" opacity="0.6" />
  <circle cx="256" cy="256" r="65" fill="none" stroke="url(#cyber-sun-gradient)" stroke-width="5" opacity="0.8" />

  <circle cx="256" cy="256" r="32" fill="url(#cyber-sun-gradient)" filter="url(#helios-blue-glow)" />

  <circle cx="360" cy="180" r="12" fill="#22d3ee" filter="url(#helios-blue-glow)" />
  <line x1="256" y1="256" x2="360" y2="180" stroke="#22d3ee" stroke-width="4" opacity="0.4" />
  
  <circle cx="170" cy="330" r="10" fill="#e8edf8" opacity="0.9" filter="url(#helios-blue-glow)" />
  <circle cx="220" cy="130" r="7" fill="#3b82f6" opacity="0.8" />
  <circle cx="340" cy="350" r="9" fill="#22d3ee" opacity="0.5" />
</svg>

**Multi-Scan Intelligence Platform** — A professional Nmap XML visualizer built for red teamers and pentesters.

> Inspired by the work of [sumanrox](https://sumanrox.github.io/)  
> Built by [The-Psypher](https://github.com/The-Psypher) & [Adrilaw](https://github.com/Adrilaw)

---

## What Is It?

NMAP Helios merges the best of two tools into a single, zero-dependency HTML file:

- **FastMap** — single-scan visualizer with per-port enumeration tracking and PDF reporting
- **Nmap Multi-Scan Visualizer** — multi-file comparison, scan diffing, and service analysis

The result is a fully self-contained `.html` file you can open in any browser — no server, no install, no dependencies to fetch (except two CDN scripts for Chart.js and jsPDF).

---

---

## Features

### 📂 Multi-Scan Loading
- Load one or many Nmap XML files simultaneously
- Each scan gets a color-coded tab
- A **Merged** view aggregates all scans into a single unified dataset

### 🔬 Scan Comparison & Diffing
- Side-by-side stat cards per scan (hosts, open ports, unique ports, services)
- **Auto-diff**: highlights new hosts and gone hosts between the first and last scan
- Scan timestamps shown when available in the XML

### ⚡ Enumeration Tracking (per-scan mode)
- Mark each open port as `PENDING` or `DONE` per host
- Progress bar showing overall enumeration completion
- Bulk actions: set all ports to PENDING or DONE at once

### 🎯 Risk Intelligence
- Built-in vulnerability database covering 20+ critical ports (FTP, Telnet, SMB, RDP, VNC, Redis, MongoDB, etc.)
- Risk levels: CRITICAL / HIGH / MEDIUM / LOW / INFO
- Risk score aggregated across the entire scan for a headline number
- Click any vulnerable port to see all affected hosts

### 📊 Visual Analytics
- Horizontal bar chart: top services by count
- Vertical bar chart: top open ports, color-coded by risk level
- Charts are theme-aware (dark/light)
- Click chart bars to filter the host inventory

### 🖥️ Host Inventory
- Expandable accordion per host
- Single-scan mode: shows per-port risk tags + PENDING/DONE toggle
- Multi-scan mode: shows full port table with product/version info
- Scan-source dots on each host (in merged view)
- Copy IP, view raw XML per host

### 🔍 Search & Filter
- Search by IP, hostname, port number, or service name
- Sidebar click-to-filter by port or service
- Keyboard shortcut `/` to focus search

### 💾 Export Options
- **JSON** — full scan data for all loaded sessions
- **CSV** — port report with risk level and enum status columns
- **TXT** — clean IP list from the active view
- **PDF** — professional security assessment report with executive summary, risk distribution, and per-port findings

### 🌓 Theme
- Dark (default) and light themes
- Preference saved to `localStorage`

---

## Usage

1. Open http://nmaphelios.redparakeet.org/ in any modern browser.
2. Drag and drop one or more Nmap XML files, or click **Add Scan**.
3. Use the **Merged** tab to see all scans combined.
4. Click ports or services in the sidebar to filter hosts.
5. In single-scan mode, click **PENDING/DONE** per port to track enumeration.
6. Click **Export** to download a PDF report or CSV.

> 💡 Hit the **Load Example** button to try it instantly with two synthetic scans that include a diff.

---

## Generating Nmap XML

```bash
# Basic scan
nmap -sV -oX output.xml 192.168.1.0/24

# Aggressive scan with OS detection
nmap -A -oX output.xml 192.168.1.0/24

# Full port scan
nmap -sV -p- -oX output.xml 192.168.1.0/24
```

Load the resulting `.xml` file directly into Helios.

---

## Built With

- Vanilla JS (no framework, no build step)
- [Chart.js 4.4](https://www.chartjs.org/) — charts
- [jsPDF 2.5](https://github.com/parallax/jsPDF) — PDF export
- [JetBrains Mono](https://www.jetbrains.com/legalnotice/font/) + [Syne](https://fonts.google.com/specimen/Syne) — typography


---

## Authors

- **[The-Psypher](https://github.com/The-Psypher)** — [LinkedIn](https://www.linkedin.com/in/prajesh-rajcoomar-140a693b5)
- **[Adrilaw](https://github.com/Adrilaw)** — [LinkedIn](https://www.linkedin.com/in/dodin-mel-adrien-lawrence-enzo-5568b91b5/)

Inspired by the security tooling work of **[sumanrox](https://sumanrox.github.io/)**

---

# 📝 License
Nmap-Helios is licensed under the [GNU General Public License](LICENSE) and the [Nmap-Helios Commercial License](C-LICENSE)- see the LICENSE file for details

---

## Disclaimer

This tool is intended for **authorized security assessments only**. Do not use against systems you do not have explicit permission to test. The authors accept no liability for misuse.
