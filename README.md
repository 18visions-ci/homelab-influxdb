# homelab-influxdb

This repository contains Ansible playbooks and roles for installing and configuring InfluxDB 2.x on Debian-based systems. It automates the setup of InfluxDB, including repository configuration, installation, and initial database setup with organization, bucket, token, and retention policy.

## Structure

- `main.yaml`: Main Ansible playbook to install and configure InfluxDB.
- `roles/influxdb_install`: Installs InfluxDB and sets up the service.
- `roles/influxdb_configure`: Waits for InfluxDB to become available and performs initial setup.

## Requirements

- Ansible 2.9+
- Debian-based target host(s)
- InfluxDB 2.x

## Usage

1. **Set environment variables** for sensitive values:
   ```sh
   export influxdb_admin_pw='your_admin_password'
   export influxdb_tkn='your_influxdb_token'
   ```

2. **Run the playbook**
   ```sh
   ansible-playbook -i <your_inventory> main.yaml
   ```
   Replace <your_inventory> with your Ansible inventory file.

Variables
You can override the following variables in your inventory or via extra vars:

influxdb_admin: Admin username (default: admin)
influxdb_admin_password: Admin password (from env)
influxdb_org: Organization name (default: homelab)
influxdb_bucket: Bucket name (default: esp32_data)
influxdb_token: Admin token (from env)
influxdb_retention: Retention period (default: 17520h)
influxdb_version: InfluxDB version (default: 3.0.3)