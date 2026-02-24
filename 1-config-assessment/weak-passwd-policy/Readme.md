# Weak Password Policy Assessment

## Objective
To demonstrate Wazuh Configuration Assessment detects weak password policy settings.

---

## Lab Setup

- Windows agent reporting to Wazuh
- Configuration Assessment enabled
- CIS Benchmark policy applied

---

## Procedure

1. On the Windows agent, made password policy insecure:

```cmd
Open Cmd Terminal as Adminitrative and then Run the below cmd.
net accounts /minpwlen:0

Queries:
data.sca.check.title:password
data.sca.check.result:failed/passed
data.sca.check.id:51502
data.sca.check.agentid:001
data.sca.check.agentip:192.168.56.3
