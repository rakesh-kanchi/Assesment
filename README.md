# Assessment

This is my take-home assessment.
## Setup

To set up this monitoring system:

1. **Install Docker**:  
   Follow the official Docker installation guide for your platform.

2. **Install Docker Compose Plugin**:  
   Install the Docker Compose plugin to manage multi-container Docker applications.

3. **Run Docker Compose**:  
   Navigate to the project directory and run the following command to start the containers:
   ```bash
   docker-compose up

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

Grafana is connected to Prometheus for visualizing the metrics.

![dashboard](https://github.com/user-attachments/assets/ed5d055b-4085-429d-baaa-84b4043a19e2)

