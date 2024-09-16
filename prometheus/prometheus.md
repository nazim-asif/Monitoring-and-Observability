# Prometheus

1. Download prometheus from [Link text](https://prometheus.io/download/)
2. service of prometheus
```
[Unit]
Description=Prometheus
Documentation=https://prometheus.io/docs/introduction/overview/
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
User=prometheus
Group=prometheus
ExecReload=/bin/kill -HUP $MAINPID
ExecStart=/usr/local/bin/prometheus \
--config.file=/etc/prometheus/prometheus.yml \
--storage.tsdb.path=/var/lib/prometheus \
--web.console.templates=/etc/prometheus/consoles \
--web.console.libraries=/etc/prometheus/console_libraries \
--web.listen-address=0.0.0.0:9090 \
--web.external-url=

SyslogIdentifier=prometheus
Restart=always

[Install]
WantedBy=multi-user.target
EOF

```

3. Command for setup 

```agsl
sudo groupadd --system prometheus
sudo useradd -s /sbin/nologin --s[nodeExporter.md](..%2Fnode_exporter%2FnodeExporter.md)ystem -g prometheus prometheus
sudo mkdir /var/lib/prometheus
sudo mkdir -p /etc/prometheus/rules
sudo mkdir -p .etc/prometheus/rules.s
sudo mkdir -p .etc/prometheus/files_sd
sudo tar xvf prometheus-3.0.0-beta.0.linux-amd64.tar.gz 
sudo mv prometheus promtool /usr/local/bin/
prometheus --version
sudo mkdir -p /etc/promethus/rules
sudo mkdir -p /etc/prometheus/
sudo mv prometheus /etc/promethus/prometheus.yml
cd prometheus-3.0.0-beta.0.linux-amd64/
sudo mv prometheus /etc/promethus/prometheus.yml
sudo mv prometheus.yml /etc/promethus/prometheus.yml
sudo tee /etc/systemd/system/prometheus.service<<EOF
[Unit]
Description=Prometheus
Documentation=https://prometheus.io/docs/introduction/overview/
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
User=prometheus
Group=prometheus
ExecReload=/bin/kill -HUP $MAINPID
ExecStart=/usr/local/bin/prometheus   --config.file=/etc/prometheus/prometheus.yml   --storage.tsdb.path=/var/lib/prometheus   --web.console.templates=/etc/prometheus/consoles   --web.console.libraries=/etc/prometheus/console_libraries   --web.listen-address=0.0.0.0:9090   --web.external-url=

SyslogIdentifier=prometheus
Restart=always

[Install]
WantedBy=multi-user.target
EOF

sudo chown -R prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /etc/prometheus/
sudo chown -R prometheus:prometheus /etc/prometheus/*
sudo chmod -R 777 /etc/prometheus
mv /var/lib/prometheus /var/lib/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo mv /var/lib/prometheus /var/lib/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo systemctl daemin-reload
sudo systemctl start prometheus
sudo systemctl enable prometheus
sudo systemctl status prometheus


```

4. get prometheus dashboard from localhost:9090