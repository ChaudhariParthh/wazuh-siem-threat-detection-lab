# Antivirus Configuration Assessment

## Objective
Demonstrate Wazuh can detect disabled antivirus settings using the CIS Benchmark.

---

## Lab Setup

- Wazuh Manager connected to Windows agent
- Real-time Defender and related protections tested
- Configuration Assessment enabled

---

## Procedure

1. On the Windows agent:
   - Disabled Defender protections: real-time, cloud-delivery, sample submission
2. Restarted the Wazuh Agent service.
3. Opened:
   - **Endpoint Security → Configuration Assessment → Dashboard**
4. Filtered checks:
   - Search: `defender` or `antivirus`

---

## Query Examples

```text
data.sca.check.title:defender
data.sca.check.result:failed
