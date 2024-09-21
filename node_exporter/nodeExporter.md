# Node Exporter

Node Exporter is a Prometheus exporter that collects and exposes hardware and OS-level metrics such as CPU, memory, disk, and network usage from a Linux, Windows, or MacOS machine. It is widely used to monitor system health in Prometheus-based monitoring solutions.

1. Download Node Exporter:

```agsl

# Change directory to /usr/local/bin or another location where you want to keep the binary
cd /usr/local/bin

# Download the Node Exporter binary
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz

# Extract the archive
tar -xvf node_exporter-1.8.2.linux-amd64.tar.gz

# Move the binary to /usr/local/bin
mv node_exporter-1.8.2.linux-amd64/node_exporter /usr/local/bin/

# Cleanup the downloaded files
rm -rf node_exporter-1.6.1.linux-amd64.tar.gz node_exporter-1.8.2.linux-amd64


```

2. Create a Service for Node Exporter:

To ensure that Node Exporter starts automatically at boot and runs as a system service, create a systemd service file.

i. Create a systemd unit file for Node Exporter:
```agsl
sudo nano /etc/systemd/system/node_exporter.service
```

ii. Add the following content to the file:

```agsl
[Unit]
Description=Node Exporter
After=network.target

[Service]
User=node_exporter
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target

```

iii. Save the file and exit the editor.

3. Prepare User for Node Exporter:

```agsl
sudo chown -R prometheus /var/lib/node
sudo chown -R prometheus /var/lib/node/*
sudo chmod -R 775 /var/lib/node
sudo chmod -R 775 /var/lib/node/*

```

4. Create service file:

```agsl
sudo vim /etc/systemd/system/node.service
```

5. node.service file:

```agsl
[Unit]
Description=Prometheus Node Exporter
Documentation=https://prometheus.io/docs/introduction/overview/
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
User=prometheus
Group=prometheus
ExecReload=/bin/kill -HUP $MAINPID
ExecStart=/var/lib/node/node_exporter

SyslogIdentifier=prometheus_node_exporter
Restart=always

[Install]
WantedBy=multi-user.target
```

6. Start and Enable the Node Exporter Service:

```agsl
# Reload systemd to register the new service
sudo systemctl daemon-reload

# Start Node Exporter service
sudo systemctl start node_exporter

# Enable the service to start on boot
sudo systemctl enable node_exporter

sudo systemctl status node_exporter

```
7. Test Node Exporter: Node Exporter listens on port 9100 by default. You can test it by querying its /metrics endpoint using curl or your web browser.

```agsl
curl http://localhost:9100/metrics
```
8. Configure Prometheus to Scrape Node Exporter: Now, you need to tell your Prometheus server to scrape the metrics from Node Exporter.

i. Edit the Prometheus configuration file (prometheus.yml) to add the Node Exporter target.

```agsl
# prometheus.yml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['<server-ip>:9100']

```

Replace <server-ip> with the IP address or hostname of your application server where Node Exporter is running.

ii. Restart Prometheus to apply the changes:

```agsl
sudo systemctl restart prometheus

```