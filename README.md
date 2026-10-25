# SafeVault

**A Windows-based defensive security prototype for early detection of ransomware-like behavior.**

SafeVault monitors a protected directory, records file-system activity, analyzes abnormal patterns such as rapid mass modification, renaming and deletion, and produces a risk score and security alert. Detection is based on *behavior* rather than known malware signatures.

> **Status:** Semester project prototype, work in progress.
> **Institution:** National University of Computer and Emerging Sciences (FAST-NUCES), Department of Computer Science, Lahore, Pakistan

## Overview

Ransomware can rapidly modify or encrypt large numbers of files, making data unavailable to users. SafeVault identifies suspicious activity from what it *does*, so early warning is possible even without a known signature. It provides real-time monitoring of a user-selected directory, explains the evidence behind each alert, and shows the current risk level on a simple dashboard.

It is intended as a practical defensive prototype for personal and organizational Windows environments.

## Goals

- Monitor file-system activity in a protected directory on Windows.
- Detect ransomware-like behavior using measurable activity indicators and a risk-scoring engine.
- Generate timely alerts and retain evidence explaining suspicious activity.
- Provide a safe simulator for controlled ransomware-like file operations.
- Evaluate detection rate, false positives and detection time using controlled test cases.

## Features

- **File monitoring:** collects create, modify, rename and delete events in protected directories.
- **Event logging:** keeps a record of events as evidence for later review.
- **Behavioral analysis:** flags patterns such as mass modification, renaming and deletion in a short time window.
- **Risk scoring:** combines activity indicators into a risk score with tunable thresholds.
- **Alerting:** raises alerts with the evidence that triggered them.
- **Dashboard:** a simple view of the current risk level and recent alerts.
- **Test simulator:** a controlled, reversible simulator of ransomware-like file operations.

## Architecture

SafeVault uses a modular design:

```
┌────────────────┐   ┌───────────────┐   ┌───────────────────┐
│ File Monitor   │──▶│ Event Logger  │──▶│ Behavioral        │
│ (protected dir)│   │ (evidence)    │   │ Analysis          │
└────────────────┘   └───────────────┘   └─────────┬─────────┘
                                                   ▼
┌────────────────┐   ┌───────────────┐   ┌───────────────────┐
│ Dashboard      │◀──│ Alerting      │◀──│ Risk Scoring      │
└────────────────┘   └───────────────┘   └───────────────────┘

        Test Simulator ──▶ generates controlled activity for evaluation
```

## Scope and Limitations

**In scope:** defensive monitoring of ransomware-like file activity in user-selected Windows directories, including event collection, behavioral analysis, risk scoring, alert generation, event logging and a simple dashboard.

**Out of scope:** SafeVault does **not** aim to

- replace a commercial antivirus,
- recover encrypted files, or
- detect every malware family.

## Safe Testing

Testing uses only benign workloads and a controlled, **reversible** simulator. **Real ransomware is never used** in this project.

## Evaluation

The prototype is evaluated on normal and suspicious activity using:

| Metric | Description |
|---|---|
| Detection rate | Share of simulated ransomware-like runs that are detected |
| False-positive rate | Share of normal workloads wrongly flagged as suspicious |
| Detection time | Time from the start of suspicious activity to the alert |

## Getting Started

> Setup instructions will be added as the implementation is completed.

```bash
# Clone the repository
git clone https://github.com/<your-username>/SafeVault.git
cd SafeVault
```

**Requirements:** Windows 10 or later. Language and dependencies to be confirmed.

## Project Structure

> Planned layout, to be updated as the code is added.

```
SafeVault/
├── monitor/       # file-system event collection
├── analysis/      # behavioral analysis and risk scoring
├── alerts/        # alert generation and event logging
├── dashboard/     # simple security dashboard
├── simulator/     # safe, reversible test simulator
├── docs/          # proposal and documentation
└── README.md
```

## Roadmap

- [x] Initial study of requirements, ransomware behavior and behavior-based detection
- [x] Define use case and modular design
- [ ] Implement file monitoring and event logging
- [ ] Implement behavioral analysis and risk scoring
- [ ] Implement alerting and dashboard
- [ ] Build the safe simulator
- [ ] Threshold tuning and controlled experiments
- [ ] Performance evaluation and documentation
- [ ] Final in-class evaluation

## References

1. National Institute of Standards and Technology, "Guide to Malware Incident Prevention and Handling for Desktops and Laptops," NIST SP 800-83, 2005.
2. National Institute of Standards and Technology, "Computer Security Incident Handling Guide," NIST SP 800-61 Rev. 2, 2012.
3. European Union Agency for Cybersecurity (ENISA), "Ransomware: An Introduction for Policy Makers," ENISA, 2021.

## Team

| Name | Roll No. |
|---|---|
| Muhammad Hassan Lodhi | 23L-0903 |
| Sarmad Irfan | 23L-3002 |

## Disclaimer

SafeVault is an academic prototype for educational and defensive research purposes. It is not a replacement for commercial endpoint protection and comes with no guarantee of detection.
