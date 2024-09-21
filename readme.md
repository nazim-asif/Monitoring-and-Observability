# 1. Prometheus

Prometheus is an open-source systems monitoring and alerting toolkit. It is widely used for collecting, storing, and querying metrics. It provides powerful querying language (PromQL) for analyzing the metrics data.

1. Components:

i. Prometheus Server: Fetches and stores metrics data.

ii. Alertmanager: Handles alerts generated by Prometheus.

iii. Pushgateway: Allows for short-lived jobs to push metrics to Prometheus.

iv. Exporters: Collects metrics from services and systems.

2. Use Cases:

i. Performance monitoring.

ii. Resource utilization tracking (CPU, memory, disk).

iii. Custom metrics collection from applications.

iv. Alerting based on threshold conditions.


# 2. Grafana
   Grafana is an open-source data visualization and monitoring platform. It supports multiple data sources and is commonly used for creating dashboards and visualizing metrics.

1. Features:

i. Dashboards: Highly customizable and interactive dashboards.

ii. Alerts: Define alerts based on the data visualized in dashboards.

iii. Data Sources: Supports multiple data sources like Prometheus, Loki, Elasticsearch, MySQL, etc.

iv. Plugins: Extensible through plugins for additional functionalities.

2. Use Cases:

i. Real-time monitoring of infrastructure and applications.

ii. Visualization of metrics collected by Prometheus and other sources.

iii. Setting up and managing alerts.

# 3. Loki
   Loki is a log aggregation system designed to work alongside Prometheus. Unlike traditional log systems, Loki is optimized for indexing metadata like labels instead of the entire content of the logs.

1. Features:

i. Log Aggregation: Collects logs from multiple sources.

ii. Efficient Storage: Uses the same label model as Prometheus, making it very cost-effective.

iii. Querying: Allows querying logs using LogQL, which is similar to PromQL.

iv. Integration: Easily integrates with Grafana for visualization and analysis.

2. Components:

i. Loki: Central server to store and query logs.

ii. Promtail: Agent for collecting logs from different sources and forwarding them to Loki.

3. Use Cases:

i. Centralized logging for cloud-native applications.

ii. Correlating logs with Prometheus metrics for troubleshooting.

# 4. Node Exporter
   Node Exporter is a Prometheus exporter for hardware and operating system metrics exposed by *nix kernels. It’s one of the most common exporters and is used for collecting system-level metrics.

1. Metrics Provided:

i. CPU, memory, disk, and network usage.

ii. Filesystem statistics.

iii. System load and uptime.

iv. Temperature and fan speeds (on compatible systems).

2. Use Cases:

i. Monitoring the health and performance of Linux servers.

ii. Collecting system-level metrics to create infrastructure dashboards.

iii. Setting up alerts for resource exhaustion (e.g., high CPU or memory usage).

# 5. Promtail
   Promtail is an agent for collecting logs and forwarding them to Loki. It is designed to be the companion to Loki and is responsible for gathering logs from various sources.

1. Features:

i. Log Collection: Collects logs from files, systemd journal, or Docker logs.

ii. Metadata Enrichment: Attaches labels to log entries to enrich logs with metadata.

iii. Dynamic Configuration: Supports relabeling and scraping configuration changes dynamically.

2. Use Cases:

i. Collecting logs from application and system sources.

ii. Forwarding logs to Loki for storage and querying.

iii. Enriching logs with context (e.g., pod name, namespace).


# Most common architecture 

![architecture](Grafana loki.png)




