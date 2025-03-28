# Assessment

This is my take-home assessment.

## Overview

This project implements a monitoring system using **Prometheus**, **Prometheus Node Exporter**, and **Grafana** to track system-level metrics such as CPU usage, memory usage, disk usage, and network traffic.

### Key Features:
- **Real-Time Metrics Monitoring**: Collects metrics such as CPU usage, memory, disk, and network traffic from the monitored servers.
- **Alerting System**: Configures alerts in **Grafana** for important system events (e.g., CPU usage > 80% for more than 2 minutes).
- **Visualization**: Uses **Grafana** to visualize the collected metrics with custom dashboards for easy monitoring and analysis.
- **Easy Setup**: The system can be quickly set up using **Docker** and **Docker Compose**, making it portable and easy to deploy.

### Tools Used:
- **Prometheus**: A time-series database that collects and stores the metrics data.
- **Prometheus Node Exporter**: A lightweight exporter that exposes system metrics from monitored servers.
- **Grafana**: A data visualization tool used to display the metrics and set up alerts.

## Setup

To set up this monitoring system:


1. **Install Docker**:  
   Follow the official Docker installation guide for your platform:  
   [Docker Installation Guide](https://docs.docker.com/get-docker/)

2. **Install Docker Compose Plugin**:  
   Install Docker Compose by following the official guide here:  
   [Docker Compose Installation Guide](https://docs.docker.com/compose/install/)

3. **Run Docker Compose**:  
   Navigate to the project directory and run the following command to start the containers:
   ```bash
   docker compose up

---

## Monitoring Design

### Metrics to Monitor
- CPU Usage
- Memory Usage
- Disk Usage
- Network Traffic

### Tools
- Prometheus
- Prometheus Node Exporter

### Backend Storage Solution for Metrics Data
- Prometheus

![image](https://github.com/user-attachments/assets/b79508c2-4b34-4878-9ea6-9adaa31c759c)

---

## Alerts

### Setup
Alerts are set up in **Grafana** for this assessment. The specific alert configuration is for **CPU usage > 80% for 2 minutes**.

### Delivery Methods
Grafana supports several notification channels such as:
- Email
- Slack
- PagerDuty
- Google Chat
- Telegram
- AWS SNS

For this setup, **Email** has been used for delivery.

![Screenshot 2025-03-21 212416](https://github.com/user-attachments/assets/321f1465-05d0-4869-8bcc-5f9207945d10)

**Tools Used**: Grafana

---

## Implementation & Scalability

Prometheus Node Exporter automatically exports system-level metrics like CPU, memory, network, and disk usage. No custom scripts were needed.

### To make the monitoring setup more robust and scalable:
1. Install Prometheus on a separate server to ensure fault tolerance and reduce load on the main server.
2. Install Prometheus Node Exporter on the main server to export metrics.
3. Prometheus will poll the Node Exporter for the latest metrics and update its storage.
4. Even if the main server goes down, metrics will not be lost due to Prometheus running on a different server.

To monitor multiple servers:
- Assign a unique ID to each Prometheus Node Exporter instance.
- Provide the hostnames/IP addresses of all servers in the Prometheus configuration.
- Prometheus will scrape metrics from all these servers.
- For enhanced fault tolerance, deploy a replica of Prometheus on a different node.

---

## Visualization Dashboard

Grafana is connected to Prometheus for visualizing the metrics(cpu, memory, disk, network).

![dashboard](https://github.com/user-attachments/assets/ed5d055b-4085-429d-baaa-84b4043a19e2)

