# Firewall Configuration Assessment

## Objective
Verify that the Wazuh Configuration Assessment module can detect Windows Firewall settings according to CIS Benchmark.

---

## Lab Setup

- Wazuh Manager (Dashboard)
- Windows agent connected & reporting
- Configuration Assessment (SCA) enabled
- Policy: CIS Microsoft Windows 10 Enterprise Benchmark v4.0.0

---

## Procedure

1. Confirm Windows Firewall is enabled or disabled.
2. Checked Wazuh Dashboard:
   - **Endpoint Security → Configuration Assessment → Dashboard**
3. Filtered results for firewall checks:
   - Search: `firewall` or `data.sca.check.title:firewall`

---

## Query Examples

```text
data.sca.check.title:firewall
data.sca.check.result:failed
data.sca.check.id:51502
data.sca.check.agentid:001
data.sca.check.agentip:192.168.56.3

