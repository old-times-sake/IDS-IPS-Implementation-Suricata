# Lab 2: IDS/IPS Implementation with Suricata

## Project Overview
This laboratory focuses on the deployment and configuration of Suricata as an Intrusion Detection System (IDS) and Intrusion Prevention System (IPS). The project encompasses environment setup, rule management, traffic generation, and advanced log analysis.

## Technical Implementation

### Engine Configuration
* **Deployment**: Installed and initialized the Suricata engine.
* **Operational Modes**: Configured and compared passive IDS mode (monitoring) and inline IPS mode (active blocking) utilizing `af-packet` in `suricata.yaml`.
* **Observability & Logging**: Enabled multi-format logging. Configured `fast.log` for quick, real-time alert triage and `eve.json` (capturing alerts, flows, DNS, HTTP) for comprehensive SIEM integration.

### Rule Management
* **Threat Intelligence**: Updated and managed base rulesets (ET/Open) via `suricata-update`.
* **Custom Policies**: Developed and deployed local rules (e.g., explicit ICMP drops) maintained in an isolated `local.rules` file to prevent update conflicts.
* **Optimization**: Implemented thresholding mechanisms on high-volume signatures to minimize False Positives (FP) and reduce alert noise.

## Testing & Validation
* **Traffic Generation**: Synthesized network traffic utilizing `nmap` and `hping3` (TCP SYN, UDP, ICMP) to trigger specific rule matches.
* **Action Enforcement**: 
    * Verified alerting capabilities in passive mode.
    * Validated active packet dropping in inline mode, ensuring the `action=drop` status was correctly logged.
* **Log Correlation**: Correlated the synthesized network flows with the resulting alerts and drop actions recorded in the EVE JSON logs.
