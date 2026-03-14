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
