# Digital Forensics Investigation — CrypticWilds Case (Wildlife Poaching)

![Security](https://img.shields.io/badge/Security-Digital%20Forensics-blue) ![Type](https://img.shields.io/badge/Type-Court%20Report-darkblue) ![Status](https://img.shields.io/badge/Status-Completed-green)

A full digital forensic investigation conducted as part of a simulated court case involving suspected wildlife poaching in Kenya. The investigation produced a **court-admissible joint expert report** with 19 documented incidents, a verified evidence chain, and a complete digital timeline.


## Case Summary

**Case:** CrypticWilds — suspected organized wildlife poaching  
**Subject:** Sonya Macoit  
**Period of Activity:** January — February 2024  
**Evidence Sources:** Hard drive image, Canon EOS R5 camera, RAM dump

**Verdict:** Digital artifacts consistently support coordinated poaching activity — planning, field operations, and active cover-up attempts were all evidenced.

---

## Investigation Workflow

```
Acquisition             Processing               Analysis                 Reporting
───────────             ──────────               ────────                 ─────────
Physical imaging   →    Integrity check     →    Email artifacts    →     Timeline
dcfldd bit-copy         MD5 / SHA256             Browser history          19 Incidents
Read-only mode          File carving             EXIF metadata            Court report
RAM dump                Deduplication            Registry analysis        Chain of custody
                        NSRL whitelist           Volatility (RAM)         Evidence list
```


## Evidence Breakdown

| # | Type | Count | Key Findings |
|---|---|---|---|
| 1 | Images | 266 (177 unique) | Canon EOS R5 EXIF data, wildlife photos, coordinates |
| 2 | Documents | 14 | Trophy hunting PDFs, drone manuals, wildlife lists |
| 3 | Email communications | 87 | Planning, coordination, encryption key exchange |
| 4 | Internet searches | 143 | Google Earth, drone laws Kenya, hunting queries |
| 5 | Internet bookmarks | 12 | Mapping services, poaching-related resources |



## Key Incidents

| Incident | Date | Finding |
|---|---|---|
| #1 | 3 Jan 2024 | Email re: satellite imagery, drone surveillance planning |
| #2 | 3 Jan 2024 | Geographic coordinates shared (-1.4604042, 35.2205633) |
| #4 | 5 Jan 2024 | Trophy hunting PDF found on system before being emailed |
| #7 | 11 Jan 2024 | Wireshark downloaded — network monitoring capability |
| #11 | 6 Feb 2024 | Elephant photos on OneDrive; switch from drones to cameras |
| #13 | 9 Feb 2024 | Wildlife target list with dates: elephants, lions, antelope, giraffe |
| #17 | 19 Feb 2024 | Files encrypted with Kleopatra; PGP key distributed |
| #18 | 20 Feb 2024 | PGP public key shared for secure comms |
| #19 | 21 Feb 2024 | BitLocker USB, Serena Airstrip destination, email compromise concern |


## Forensic Methodology

**Static Acquisition:**
- Physical bit-by-bit image using `dcfldd` via SATA (no OS boot)
- Hash verification at acquisition and at each analysis stage (MD5 + SHA-256)
- All analysis performed on forensic copies — originals untouched

**Analysis Techniques:**
- File carving with Foremost — recovered deleted images from unallocated space
- NSRL whitelist filtering — excluded known system files
- Windows registry analysis (SAM, SYSTEM, SOFTWARE, SECURITY, NTUSER.DAT)
- RAM dump analysis with Volatility — running processes, encryption evidence
- EXIF metadata extraction — device identification, timestamp cross-referencing
- Browser history reconstruction (Firefox via MZHistoryView)
- Email artifact analysis via Autopsy + Thunderbird forensics

---

## Tools Used

| Tool | Purpose |
|---|---|
| Autopsy | Main forensic platform — emails, browser history, timeline |
| dcfldd | Physical imaging with simultaneous hash verification |
| Foremost | File carving from unallocated disk space |
| Volatility | RAM dump analysis — processes, encryption artifacts |
| ExifTool / Python EXIF Script | Image metadata extraction and device identification |
| Hivex / RipXP | Windows registry hive parsing |
| MZHistoryView / MZCacheView | Firefox browser artifact analysis |
| affuse / ewfmount | Read-only forensic image mounting |
| Autopsy NSRL | Known-good file filtering |
| Kleopatra / GPG4Win | Identified encryption tool used by suspect |
| Wayback Machine | Historical web page verification |

---

## Custom Python Tooling

A custom Python forensic reporting script was developed as part of this investigation:

**`forensics_reporter.py`** — Automated evidence report generator:
- Extracts and deduplicates images from disk images or ZIP archives
- Extracts EXIF metadata and flags timestamp anomalies (possible spoofing)
- Embeds images with SHA-256 hashes into a structured Word report
- Exports a CSV evidence log with full metadata per file
- Detects EXIF/filesystem timestamp mismatches

**`pdfToDocx.py`** — Converts PDF document exhibits into 2×2 grid Word report for court presentation.


## Report

Full joint expert court report included in this repository.

📄 [Court_Report.docx](./Court_Report.docx)


## Tools & References

- [Autopsy Digital Forensics](https://www.autopsy.com/)
- [Volatility Framework](https://volatilityfoundation.org/)
- [Foremost File Carving](http://foremost.sourceforge.net/)
- [ExifTool](https://exiftool.org/)
- [dcfldd](https://github.com/resurrecting-open-source-projects/dcfldd)
- [NIST NSRL](https://www.nist.gov/software-quality-group/national-software-reference-library-nsrl)

---

## Disclaimer

This investigation was conducted on **simulated digital evidence** provided as part of a university assignment. No real individuals, systems, or animals were involved. All findings are fictional and created for educational purposes only.
