# gNMI vs CLI Data Discrepancy Analyzer

This Python project provides a powerful and flexible tool for comparing network data retrieved via **gNMI (gRPC Network Management Interface)** and **CLI (Command Line Interface)**. It normalizes values, detects discrepancies in units, formats, and precision, and generates detailed discrepancy reports.

## 🔍 Overview

The project automates the process of:

- Loading gNMI and CLI output files
- Normalizing differences in:
  - Text case (e.g., `LINK_UP` vs `LinkUp`)
  - Units (e.g., `400G` vs `400`)
  - Precision (e.g., `43` vs `43.00`)
- Comparing the structured data field by field
- Reporting mismatches and missing data between sources

---

## 🧱 Components

### 🧩 `GNMIClient`
- Maps gNMI paths to file names
- Parses file content into structured dictionaries

### 🧩 `CLIMapper`
- Maps CLI commands to files
- Supports multiple CLI sources for a single gNMI path

### 🧩 `DataNormalizer`
- Standardizes units (KB, MB, GB to bytes)
- Normalizes strings (case, symbols, formatting)
- Handles numerical precision

### 🧩 `DataComparer`
- Compares gNMI and CLI datasets field by field
- Supports approximate matches for float values

### 🧩 `ReportGenerator`
- Generates a detailed `.txt` report
- Flags:
  - Missing fields
  - Normalized mismatches
  - Matching data

---

## 🧪 How It Works

1. **User Input**:
   - Enter a gNMI path (e.g., `/system/memory/state`)
   - Enter one or more CLI commands (e.g., `show memory`)

2. **File Mapping**:
   - Files like `gnmi_system_memory_state.txt` and `cli_show_memory.txt` should exist in the script directory

3. **Execution**:
   - The script compares values and writes a full discrepancy report

4. **Output**:
   - Console summary + `discrepancy_report.txt`

---

## 🧾 Example Use

### gNMI File: `gnmi_system_memory_state.txt`
total_memory: 4096000 available_memory: 1024000


### CLI File: `cli_show_memory.txt`
total_memory: 4096000 available_memory: 1000000


### Comparison Result:
- `total_memory`: ✅ Match
- `available_memory`: ⚠️ Difference detected




