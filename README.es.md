# Portafolio de software: Edge IoT, Integración Industrial y Observabilidad

Este portafolio reúne cuatro repositorios que cubren el ciclo completo desde el aprovisionamiento de equipos de borde hasta la ingesta de señales industriales y su observabilidad. El foco es práctico y orientado a producción: idempotencia y repetibilidad en automatización, tipado y separación de responsabilidades en Python, y flujos de Node-RED listos para operar en planta.

La línea técnica es consistente: variables de entorno y TLS recomendados para seguridad básica, control de versiones con Git/GitLab y activos versionados (playbooks, flujos, dashboards). Los README de cada proyecto están en inglés; este documento ofrece una vista general para quienes evalúan el portafolio.

## Repositorios
- Ansible IoT Edge (`../ansible-iot-edge/`)
  - Playbooks idempotentes para provisionar y mantener hosts edge (Raspberry Pi y Ubuntu). Incluye distribución de claves SSH, parches del sistema, actualización de DNS, prerrequisitos opcionales para k3s, un esqueleto de instalación de Node‑RED y utilitarios (reboot, ajustes de boot, helper SSH). Soporta Ubuntu 22.04/24.04 y Raspbian Buster.
- Node‑RED Industrial Flows (`../node-red-industrial-flows/`)
  - Flujos para ingesta y normalización de señales (PLC Modbus/S7, MQTT, HTTP) y trazabilidad RFID. Publican a InfluxDB y a una API de Empowerment con rutas controladas y compuertas de backpressure. Requiere Node‑RED 4.0 sobre Node.js 22 y paletas: node-red-contrib-influxdb, node-red-contrib-s7, node-red-contrib-queue-gate, node-red-contrib-modbus (más MQTT/HTTP built‑in).
- Observability Stack (`../observability-stack/`)
  - Dashboards Grafana (JSON) y ejemplo mínimo de Prometheus para monitoreo. Espera fuentes de datos InfluxDB y Prometheus, creadas manualmente en Grafana (sugeridas: InfluxDB_Main y Prometheus_Local). Incluye un `prometheus.yml` de ejemplo con targets de node_exporter.
- Python Data Senders (`../python-data-senders/`)
  - Utilidades y servicios en Python 3.13 para ingesta vía archivos, serie o red, con publicación a Empowerment API, InfluxDB y MQTT. Destacan: `laboratory/solidez_data_sender` (file watcher tipado), `laboratory/sort_data_sender` (flujo tipo DE_555), `rfid` (publicador Modbus→MQTT y consumidor MQTT→Influx), `pesaje_urdidora` (lector serial con fallback local) y `services/create_service_ubuntu.py` (unit files systemd).

## ¿Qué valorar aquí?
- Automatización de borde fiable: playbooks pequeños, composables, y seguros de previsualizar con `--check`.
- Integración industrial aplicada: flujos Node‑RED con conectores PLC, normalización y control de backpressure.
- Telemetría y trazabilidad: pipelines Python desacoplados (publicador/consumidor) y dashboards Grafana listos para importar.
- Buenas prácticas: tipado con dataclasses, logging rotativo, configuración por entorno, y control de versiones claro.

## Versiones de referencia
- Node‑RED 4.0 y Node.js 22
- Ubuntu 22.04 y 24.04; Raspbian Buster
- Python 3.13

## Cómo revisar (sugerencia para reclutadores)
- Leer el README de cada carpeta para alcance y configuración.
- En Ansible, revisar `playbooks/` y el inventario de ejemplo para entender la segmentación por grupos.
- En Node‑RED, importar un flujo y validar dependencias desde el Palette Manager (sin hardware, usar datos sintéticos).
- En Observability, crear las fuentes de datos y cargar los JSON para ver la estructura de paneles.
- En Python, revisar modelos, handlers y watchers para observar tipado, separación de responsabilidades y manejo de errores.

## Licencia y contacto
- Licencia: MIT (mención breve en cada repositorio).
- Contacto: ver perfil para LinkedIn o email.

