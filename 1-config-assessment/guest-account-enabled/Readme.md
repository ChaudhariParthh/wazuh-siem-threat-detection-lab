# Guest Account Security Assessment

## Objective
To verify Wazuh Configuration Assessment can detect insecure Windows Guest account settings.

---

## Lab Setup

- Connected Windows agent reporting to Wazuh
- SCA running with CIS Benchmark

---

## Procedure

1. On the Windows agent, enabled the Guest account:

```cmd
net user guest /active:yes


Queries:
data.sca.check.title:guest
data.sca.check.result:failed/passed
data.sca.check.id:51502
data.sca.check.agentid:006
data.sca.check.agentip:192.168.56.3
