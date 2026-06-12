# Deployment Guide

## Prerequisites

* Ubuntu Linux Server
* Docker
* Docker Compose
* Network connectivity to monitored infrastructure

---

## Clone Repository

```bash
git clone https://github.com/<username>/enterprise-observability-platform.git
cd enterprise-observability-platform
```

---

## Configure Prometheus Targets

Edit:

```text
prometheus/targets/linux.yml
prometheus/targets/proxmox.yml
```

Add required target servers and Proxmox nodes.

---

## Configure Proxmox Exporter

Edit:

```text
proxmox-exporter/pve.yml
```

Configure:

* API Endpoint
* User
* API Token
* Permissions

---

## Configure Google Chat Integration

Create an Incoming Webhook inside Google Chat.

Update:

```text
grafana → Contact Points
```

Configure:

* Webhook URL
* Notification Policy
* Alert Routing

---

## Deploy Stack

```bash
docker compose -f docker-compose/docker-compose.yml up -d
```

---

## Verify Containers

```bash
docker ps
```

Expected Services:

* Prometheus
* Grafana
* Alertmanager
* Proxmox Exporter

---

## Access URLs

Prometheus:

```text
http://<server-ip>:9090
```

Grafana:

```text
http://<server-ip>:3000
```

Alertmanager:

```text
http://<server-ip>:9093
```

---

## Import Dashboards

Grafana

Dashboard → Import

Import JSON files from:

```text
grafana/dashboards/
```

---

## Configure Alert Rules

Navigate to:

```text
Grafana → Alerting → Alert Rules
```

Import or create rules from:

```text
prometheus/rules/
```

---

## Validation

Verify:

* Metrics are collected
* Dashboards are populated
* Alert rules are evaluating
* Notifications reach Google Chat

Deployment completed successfully.

