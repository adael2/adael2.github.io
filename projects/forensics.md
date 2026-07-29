# Forensics Investigation Lab

## Objective
Perform a digital forensics investigation by analyzing Windows artifacts, including NTUSER.DAT, RecentDocs, and 7‑Zip File Manager metadata, to identify user activity, file access patterns, and potential evidence relevant to an incident.

## Tools
Windows Forensics Tools  
Registry Explorer  
7‑Zip File Manager  
Hex editors  
Event log viewers

## Procedure

### 1. NTUSER.DAT Analysis
- Load NTUSER.DAT using Registry Explorer.
- Inspect user-specific registry hives:
  - UserAssist
  - RunMRU
  - RecentDocs
- Identify executed programs, opened files, and user interaction patterns.

### 2. RecentDocs Enumeration
- Navigate to `Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RecentDocs`.
- Extract:
  - File names
  - Extensions
  - Last accessed timestamps
- Reconstruct user activity timeline based on document access.

### 3. UserAssist Investigation
- Review `Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\UserAssist`.
- Decode ROT13‑encoded entries.
- Identify:
  - Application execution history
  - Run counts
  - Last execution timestamps

### 4. 7‑Zip File Manager Artifact Review
- Inspect 7‑Zip FM history files.
- Identify:
  - Opened archives
  - Extracted files
  - Paths and timestamps
- Correlate findings with NTUSER.DAT activity.

### 5. Timeline Correlation
- Combine NTUSER.DAT, RecentDocs, UserAssist, and 7‑Zip FM data.
- Build a unified activity timeline showing:
  - File access
  - Application execution
  - Archive manipulation
  - User behavior patterns

### 6. Evidence Validation
- Cross‑reference timestamps with system logs.
- Validate consistency across artifacts.
- Document anomalies or suspicious behavior.

## Findings
- NTUSER.DAT revealed detailed user activity, including executed applications and accessed files.
- RecentDocs provided a clear timeline of document interaction.
- UserAssist entries confirmed program execution frequency and timestamps.
- 7‑Zip FM artifacts exposed archive access and file extraction behavior.
- Correlation of all artifacts produced a reliable reconstruction of user actions.

## Conclusion
This forensics lab demonstrates practical skills in Windows artifact analysis, 
including registry hive inspection, metadata extraction, timeline reconstruction, and evidence correlation. 
It reflects understanding of core concepts used in DFIR, incident response, and digital investigations.
