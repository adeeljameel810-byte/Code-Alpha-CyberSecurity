# Network-Based Intrusion Detection System (NIDS) Setup

## Overview
This guide explains how to set up a network-based intrusion detection system using Snort or Suricata, configure detection rules and alerts, monitor traffic continuously, implement response mechanisms, and optionally visualize detected attacks.

## 1. Choose a Tool

- **Snort**: widely-used signature-based NIDS
- **Suricata**: modern IDS/IPS with multi-threading and protocol parsing

## 2. Install the IDS

### Snort Installation

1. Install dependencies:
   - `libpcap`, `pcre`, `libdnet`, `daq`, and build tools
2. Download Snort from the official site or package manager.
3. Configure the base directory and rules location.

### Suricata Installation

1. Install dependencies:
   - `libpcap`, `libyaml`, `libnet1`, `libhtp`, and build tools
2. Install from package manager or source.
3. Configure `suricata.yaml` for your interface and logging.

## 3. Configure Rules and Alerts

### Rule Source

- Use official rule sets like Snort VRT or Emerging Threats
- Start with a small, relevant rule set to reduce noise

### Basic Rule Configuration

- Snort rules are stored in `.rules` files
- Suricata also supports Snort rules via `suricata.yaml`

Example rule pattern:

```text
alert tcp any any -> any 80 (msg:"Possible HTTP exploit"; flow:to_server,established; content:"GET"; sid:1000001; rev:1;)
```

### Alert Output

- Snort: configure `alert.fast`, `fast.log`, `full.log`, or unified2 output
- Suricata: configure EVE JSON logging and alert outputs

### Rule Tuning

- Disable or tune noisy rules
- Use thresholding and suppression to reduce false positives
- Customize rules for your environment and asset profiles

## 4. Monitor Traffic Continuously

### Deployment Modes

- **Inline**: Suricata in IPS mode to block traffic
- **Passive**: Snort/Suricata monitors mirrored traffic from a network tap or SPAN port

### Continuous Monitoring

- Run the IDS as a service or daemon
- Ensure it starts on boot
- Monitor CPU, memory, and packet drop statistics

### Logs and Alerts

- Review alert logs regularly
- Use log rotation to manage disk usage
- Save detailed packet captures for analysis if needed

## 5. Implement Response Mechanisms

### Manual Response

- Investigate alerts promptly
- Verify suspicious activity before action
- Isolate affected hosts or segments if needed

### Automated Response

- Use Suricata in IPS mode to drop or reject traffic
- Integrate with firewall rules, e.g. `pf`, `iptables`, or `firewalld`
- Trigger scripts from alert events to block IPs or notify teams

### Incident Workflow

- Triage the alert
- Identify affected systems
- Contain, eradicate, and recover
- Document findings and actions

## 6. Visualization and Dashboards

### Recommended Visualization Tools

- **ELK Stack** (Elasticsearch, Logstash, Kibana)
- **Grafana** with time-series databases like InfluxDB
- **TheHive** / **Cortex** for incident response

### Example Setup

1. Forward IDS alerts to Elasticsearch or another log store
2. Create dashboards for:
   - alert counts by severity
   - top source IPs
   - destination ports
   - rule categories triggered
3. Use graphs and heatmaps to spot anomalies over time

## 7. Best Practices

- Keep rule sets updated
- Tune alerts for your environment
- Monitor system performance and packet drops
- Maintain proper logging and retention policies
- Regularly review and test IDS detections

## 8. Example Commands

### Start Snort

```bash
snort -c /etc/snort/snort.conf -i eth0 -A console
```

### Start Suricata

```bash
suricata -c /etc/suricata/suricata.yaml -i eth0
```

### Check Suricata stats

```bash
suricatasc stats
```

## 9. Documentation and Remediation

- Document detected intrusions with timestamps, rules triggered, and source/destination details
- Record response actions taken and follow-up steps
- Review and update IDS configuration after each significant incident

## Conclusion
A network-based intrusion detection system combines signature rules, continuous monitoring, and response processes. With proper configuration, tuning, and visualization, Snort or Suricata can help detect and mitigate suspicious network activity.
