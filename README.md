# WiFiScan

## 🇬🇧 Description

**WiFiScan** is a tool for mass scanning of IP ranges and ports:
- checking router availability,
- login/password dictionary authentication,
- rotating User-Agent headers,
- saving results in CSV format,
- optional upload of results to a server.

This repository contains prebuilt **Windows binaries** and helper text files.

---

## 🔧 Quick Start

### 1. Prepare targets
Create `targets.txt` with seed IPs/domains (one per line):
```
1.1.1.1
example.com
8.8.8.8
```

### 2. Generate ranges
Generate `ranges.txt` with **near_ranges**:
```bash
near_ranges.exe --file=targets.txt --show-hops --radb --outfile ranges.txt
```

Explanation:
- `--file=targets.txt` — input IPs/domains;
- `--show-hops` — display discovered hops/neighbor networks;
- `--radb` — augment ranges with RADB routing registry data;
- `--outfile ranges.txt` — save computed ranges.

### 3. Run the scanner
```bash
wifiscan.exe ^
  -ranges-file ranges.txt ^
  -ports-file ports.txt ^
  -auth-file auth.txt ^
  -ua-file user_agent.txt
```

Results are stored in `out/` as `scan_<timestamp>.csv`.

---

## 📂 Structure
- `wifiscan.exe` — main scanner binary (Windows).
- `near_ranges.exe` — range generator from `targets.txt`.
- `ports.txt` — ports to scan.
- `ranges.txt` — ranges to scan (generated).
- `auth.txt` — login/password dictionary.
- `user_agent.txt` — sample User-Agents.
- `targets.txt` — initial seeds.
- `out/` — CSV scan results.

---

## 📝 Sample file formats

**`ports.txt`**
```
80,443
8080
```

**`ranges.txt`**
```
# example
192.168.1.1
192.168.1.10-192.168.1.12
10.0.0.0/30
```

**`auth.txt`**
```
# login:password
admin:admin
admin:password
user:user
```

**`user_agent.txt`**
```
# desktop
Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
# mobile
Mozilla/5.0 (Linux; Android 12; SM-G991B) ...
```

---

## 📜 
