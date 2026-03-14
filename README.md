# Infrastructure Monitoring System (Prometheus + Grafana)

A production-style infrastructure monitoring system built using **Prometheus, Grafana, Alertmanager, and Node Exporter**.

This project demonstrates how to monitor Linux servers, visualize metrics, and trigger alerts when system resources cross defined thresholds.

---

# Architecture
![Architecture Diagram](./screenshots/Architecture.png)

---

## Tech Stack
- **Prometheus** - Metrics collection & storage
- **Grafana** - Visualization & dashboards
- **Alertmanager** - Alert routing & notifications
- **Node Exporter** - Linux system metrics

---

# Metrics Monitored

| Metric | Description |
|------|-------------|
| CPU Utilization | CPU usage percentage |
| CPU Available | Remaining CPU capacity |
| Memory Utilization | Memory usage percentage |
| Memory Available | Remaining RAM |
| Disk Utilization | Disk usage percentage |
| Disk Available | Remaining disk space |
| Network Traffic | Network I/O monitoring |
| System Load | Server load averages |
| Node Status | Node exporter health |

---

# Alert Rules
The monitoring system includes the following alerts:

### Node Exporter Status
Node Exporter Down for 1 minute

### High CPU Usage
CPU usage > 90% for 2 minutes

### High Memory Usage
CPU usage > 90% for 2 minutes

### High Disk Usage
Disk usage > 90% for 2 minutes

# Project Structure
```
.
├── alertmanager.yml
├── alert.rules.yml
├── dashboards
│   └── Server Monitoring.json
├── docker-compose.yml
├── prometheus.yml
├── README.md
└── screenshots
    ├── AlertManager.png
    ├── Alert_rules.png
    ├── Architecture.png
    ├── CPU_Utilization.png
    ├── Dashboard.png
    ├── Email_alert.png
    ├── firing_state.png
    └── Resolved_email.png
```
---

## Dashboard
### Server Monitoring Overview
<img src="./screenshots/Dashboard.png" alt="Dashboard Overview" width="800"/>

---

## Alerting

### High CPU Utilization (Grafana)
<img src="./screenshots/CPU_Utilization.png" alt="Prometheus Alert Rules" width="800"/>

### Alert Rules (Prometheus)
<img src="./screenshots/Alert_rules.png" alt="Prometheus Alert Rules" width="800"/>

### Alert Firing state (Prometheus)
<img src="./screenshots/firing_state.png" alt="Prometheus Alert Rules" width="800"/>

### Alerts in Alertmanager
<img src="./screenshots/AlertManager.png" alt="Alertmanager Firing" width="800"/>

### Email Notifications
<img src="./screenshots/Email_alert.png" alt="CPU Warning Email" width="800"/>
<img src="./screenshots/Resolved_email.png" alt="CPU Warning Email" width="800"/>

---

# Setup Instructions

## Prerequisites
- Docker & Docker Compose installed
- A Linux target server (VM) with Node Exporter installed

---
### 1. Clone the Repository
```bash
git clone https://github.com/AniketKasurde/infrastructure-monitoring-system.git
cd infrastructure-monitoring-system
```
### 2. Configure Prometheus
Edit `prometheus.yml` and update the target IP with your server's IP:
```yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['YOUR_SERVER_IP:9100']
```
### 3. Configure Alertmanager
Edit `alertmanager.yml` and update with your Gmail credentials:
```yaml
global:
  smtp_from: 'your-email@gmail.com'
  smtp_auth_username: 'your-email@gmail.com'
  smtp_auth_password: 'your-app-password'
```
### 4. Start the Stack
```bash
docker compose up -d
```
### 5. Install Node Exporter on Target Server
```bash
# Download & RUN Node Exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.10.2/node_exporter-1.10.2.linux-amd64.tar.gz
tar xvfz node_exporter-1.10.2.linux-amd64.tar.gz
cd node_exporter-1.10.2.linux-amd64
./node_exporter
```

### 6. Access the Services

| Service | URL |
|---------|-----|
| Prometheus | http://localhost:9090 |
| Grafana | http://localhost:3000 |
| Alertmanager | http://localhost:9093 |

> Default Grafana login: **admin / admin**

### 7. Import Grafana Dashboard
1. Open Grafana → **Dashboards → Import**
2. Upload the file from `dashboards/Server Monitoring.json`
3. Select **Prometheus** as the data source
4. Click **Import**

## Verify Everything is Working
```bash
# Check all containers are running
docker ps

# Check Prometheus targets
# Go to http://localhost:9090/targets
# All targets should show as UP
```
## Author

**Aniket Kasurde**
[GitHub](https://github.com/AniketKasurde) | [LinkedIn](https://www.linkedin.com/in/aniket-kasurde/)
