# GrayLog_Metrics
GrayLog + Prometheus + Grafana

LAB 實作使用Graylog Prometheus exporter 匯出指標
再用Prometheus 收取指標資料再使用Grafana呈現圖表

GrayLog版本 : 5.1.3
請用5版以上內建支援Prometheus exporter不需要額外裝套件

開啟以下參數
```yml
# Enable Prometheus exporter HTTP server.
# Default: false
prometheus_exporter_enabled = true
 
# IP address and port for the Prometheus exporter HTTP server.
# Default: 127.0.0.1:9833
prometheus_exporter_bind_address = 0.0.0.0:9833
```

最後會輸出Metrics在以下路徑
http://localhost:9833/metrics/api/prometheus
將此路徑設置於Prometheus.yml
```yml
  - job_name: 'graylog'
    metrics_path: '/api/metrics/prometheus'
    static_configs:
      - targets: ["localhost:9833"]
```
在自行調整面板
