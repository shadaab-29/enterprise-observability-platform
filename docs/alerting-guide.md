# Alerting Guide

## Alerting Architecture

Prometheus collects metrics from monitored infrastructure.

Grafana evaluates alert conditions and generates notifications.

Google Chat receives notifications through configured webhooks.

Flow:

Infrastructure → Prometheus → Grafana Alert Rules → Notification Policy → Google Chat

---

## Evaluation Settings

### Evaluation Group

```text
infra-admin
```

### Evaluation Interval

```text
1 Minute
```

### Pending Period

```text
1 Minute
```

### Keep Firing

```text
0 Seconds
```

---

## Alert Rules

### ProxmoxHighMemory

Threshold:

```text
75%
```

Purpose:

Detect excessive memory utilization on Proxmox nodes.

---

### ProxmoxHighCPU

Threshold:

```text
80%
```

Purpose:

Detect excessive CPU utilization on Proxmox nodes.

---

### ProxmoxHighDisk

Threshold:

```text
80%
```

Purpose:

Detect excessive disk utilization on Proxmox nodes.

---

### VMHighMemory

Threshold:

```text
80%
```

Purpose:

Detect excessive memory utilization inside virtual machines.

---

### VMHighCPU

Threshold:

```text
80%
```

Purpose:

Detect excessive CPU utilization inside virtual machines.

---

### LinuxHostDown

Purpose:

Detect unavailable Linux servers.

---

### ProxmoxNodeDown

Purpose:

Detect unavailable Proxmox hypervisors.

---

### VMDown

Purpose:

Detect stopped or unavailable virtual machines.

---

## Notification Routing

Default Policy

↓

On-Prem-Infra_Alert

↓

Google Chat Webhook

---

## Alert Lifecycle

Normal

↓

Pending

↓

Alerting

↓

Notification Sent

↓

Resolved

---

## Alert Validation

To validate alerting:

1. Create a temporary test rule.
2. Trigger threshold condition.
3. Verify alert enters Alerting state.
4. Verify Google Chat notification delivery.
5. Verify automatic resolution notification.

---

## Best Practices

* Keep evaluation intervals short.
* Avoid excessive alert noise.
* Use meaningful alert names.
* Separate warning and critical alerts.
* Regularly review thresholds.
* Maintain notification routing policies.

The alerting framework provides proactive monitoring and rapid incident awareness for infrastructure operations.

