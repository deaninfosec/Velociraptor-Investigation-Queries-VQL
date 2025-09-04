# Velociraptor VQL Query Collection

A curated repository of **Velociraptor Query Language (VQL)** artifacts used for **DFIR** and **threat hunting**.

Built to support rapid, repeatable investigations using the open-source [Velociraptor](https://www.velociraptor.app/) DFIR platform.

---

## Purpose

This repository provides ready-to-use and customizable VQL artifacts to:

- Perform host-based forensics at scale
- Detect attacker behaviors using MITRE ATT&CK-aligned techniques
- Accelerate incident response workflows
- Serve as a reference and contribution hub for blue teams and DFIR analysts

---

## What is VQL?

**VQL (Velociraptor Query Language)** is a powerful and flexible language used by Velociraptor to query forensic data from endpoints in real time. It allows you to:

- Collect logs, artifacts, and registry data
- Parse MFT, prefetch, shimcache, and event logs
- Hunt for patterns across fleets of endpoints
- Build automated workflows for containment and analysis

---

## Repository Structure

The repo is organized by investigative domain and technique:

- `OS_Artifacts/` — MFT, Prefetch, Amcache, Shimcache, Event Logs, etc.
- `Persistence/` — Autoruns, Registry Run Keys, Scheduled Tasks
- `Lateral_Movement/` — RDP usage, WMI, PsExec detection
- `Credential_Access/` — LSASS access, SAM/SECURITY hives
- `Malware_Indicators/` — Known malicious paths, LOLBins, scripts
- `Cloud_Telemetry/` — Azure/OneDrive/Google Drive indicators (if applicable)
- `Behavioral_Hunts/` — Process anomalies, parent-child process logic
- `Collection_Tactics/` — Clipboard scraping, screenshot tools
- `Data_Exfil/` — Zip tools, file uploads, outbound spikes
- `Custom_Tools/` — Detection of tools like Cobalt Strike, Sliver, Velociraptor itself
- `Utility/` — System triage, log extraction, enrichment helpers

---

## How to Use

1. Open your Velociraptor console (`https://yourserver:8889`)
2. Navigate to the **Artifacts** or **Notebooks** section.
3. Import the `.vql` file or copy-paste the query into a new artifact.
4. Test and validate against a controlled endpoint.
5. Launch a hunt across selected endpoints or the entire fleet.

> Some queries may require administrative access or elevated permissions on the endpoint.

---

## Detection Philosophy

This repository emphasizes:

- **Behavior over signature** — detect how attackers operate, not just which tools they use
- **Forensic richness** — extract deep, raw data for timeline reconstruction
- **Scalability** — queries are built to perform well at fleet scale
- **Modularity** — many VQLs are designed to be chained or reused

---

## Sample Query Preview

```vql
SELECT *
FROM artifact.Windows.Detection.ProcessCreation
WHERE CommandLine =~ '.*mimikatz.*'
