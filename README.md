# Software Portfolio: Edge IoT, Industrial Integration, and Observability

This portfolio brings together four repositories that cover the end‑to‑end path from edge device provisioning to industrial data ingestion and visibility. The focus is practical and production‑oriented: idempotent automation, typed and separated concerns in Python, and Node‑RED flows ready for shop‑floor use.

The technical throughline is consistent: environment variables and TLS recommended for basic security, version control with Git/GitLab, and versioned assets (playbooks, flows, dashboards). Individual project READMEs are in English; this document offers a recruiter‑friendly overview.

## Repositories
- Ansible IoT Edge (`../ansible-iot-edge/`)
  - Idempotent playbooks to provision and maintain edge hosts (Raspberry Pi -Raspbian and Ubuntu- and Ubuntu servers). Includes SSH key distribution, system patching, DNS updates, optional k3s prerequisites, a Node‑RED install scaffold, and utilities (reboot, boot tweaks, SSH helper). Supports Ubuntu 22.04/24.04 and Raspbian Buster.
- Node‑RED Industrial Flows (`../node-red-industrial-flows/`)
  - Flows for ingestion and normalization of industrial signals (PLC Modbus/S7, MQTT, HTTP) and RFID traceability. They publish to InfluxDB and an Empowerment API with controlled routes and backpressure gates. Requires Node‑RED 4.0 on Node.js 22 and palettes: node-red-contrib-influxdb, node-red-contrib-s7, node-red-contrib-queue-gate, node-red-contrib-modbus (plus built‑in MQTT/HTTP).
- Observability Stack (`../observability-stack/`)
  - Grafana dashboards (JSON) and a minimal Prometheus example for monitoring. Expects InfluxDB and Prometheus data sources created manually in Grafana (suggested names: InfluxDB_Main and Prometheus_Local). Includes an example `prometheus.yml` with node_exporter targets.
- Python Data Senders (`../python-data-senders/`)
  - Python 3.13 utilities and services to ingest via files, serial, or network and publish to Empowerment API, InfluxDB, and MQTT. Highlights: `laboratory/solidez_data_sender` (typed file watcher), `laboratory/sort_data_sender` (DE_555‑style stream), `rfid` (Modbus→MQTT publisher and MQTT→Influx consumer), `pesaje_urdidora` (serial scale reader with local fallback), and `services/create_service_ubuntu.py` (systemd unit files).

## What to Value
- Reliable edge automation: small, composable playbooks with safe `--check` previews.
- Applied industrial integration: Node‑RED flows with PLC connectors, normalization, and backpressure control.
- Telemetry and traceability: decoupled Python pipelines and Grafana dashboards.

## Reference Versions
- Node‑RED 4.0 and Node.js 22
- Ubuntu 22.04 and 24.04; Raspbian Buster
- Python 3.13

## How to Review
- Read each folder’s README for scope.
- In Ansible, review `playbooks/` and the example inventory to understand group targeting.
- In Node‑RED, import a flow and validate dependencies via the Palette Manager.
- In Observability, import the JSON to review dashboard structure.
- In Python, review models, handlers, and watchers for typing, separation of concerns, and error handling.

## License and Contact
- License: MIT (brief note in each repository).
- Contact: see profile for LinkedIn or email.

