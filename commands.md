# Suricata IDS/IPS - Command Reference

## 1. Installation & Setup
# Install Suricata engine
sudo apt install suricata

# Verify installation and check version
suricata -V

# Download and update rulesets (Emerging Threats Open)
sudo suricata-update

## 2. Configuration & Validation
# Test the configuration file for syntax errors
sudo suricata -T -c /etc/suricata/suricata.yaml -i eth0

# Edit main configuration file (to enable fast.log and eve.json)
sudo nano /etc/suricata/suricata.yaml

# Restart the service to apply changes
sudo systemctl restart suricata

## 3. Custom Rule Deployment (local.rules)
# Navigate to the rules directory
cd /var/lib/suricata/rules

# Edit local rules file
sudo nano local.rules

# Example rule used in the lab to drop/alert on ICMP traffic:
# drop icmp any any -> any any (msg:"LAB DROP ICMP"; itype:8; sid:1000001; rev:1;)

## 4. Log Analysis & Observability
# Real-time monitoring of fast.log
sudo tail -f /var/log/suricata/fast.log

# Extract specific threat notifications (alerts) from logs
cat /var/log/suricata/fast.log | grep "ALERT"
cat /var/log/suricata/eve.json | grep "ALERT"
