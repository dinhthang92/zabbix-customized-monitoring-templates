# Template Huawei AC6000 WLAN Discovery

Zabbix 7 template for monitoring Huawei AC6000 wireless controllers over SNMP.

It provides low-level discovery for access points, radios, VAPs, wireless clients, and controller interfaces, with built-in graphs and triggers for common operational issues.

## What it monitors

- Controller identity and uptime
- Total AP count, joined AP count, and associated wireless clients
- Discovered APs
- AP CPU, memory, temperature, state, software version, hardware version, and online user count
- Discovered radios per AP
- Radio status, channel, bandwidth, and associated users
- Discovered VAPs per AP/SSID
- VAP status, client count, and ESS profile
- Discovered wireless clients
- Client AP name, SSID, band, channel, RX/TX rates, status, and received power
- Discovered controller interfaces
- Interface admin status, operational status, traffic, and error counters

## Discovery rules

This template uses SNMP LLD to discover:

- APs from the Huawei WLAN AP table
- Radios from the Huawei WLAN radio table
- VAPs from the Huawei WLAN VAP table
- Wireless clients from the Huawei WLAN station table
- Interfaces from `IF-MIB::ifDescr`

Discovered entities are kept for a configurable lifetime so the host remains clean when objects disappear.

## Built-in alerts

The template includes trigger prototypes and host-level triggers for:

- AP state not normal
- Missing AP state data by SNMP
- AP CPU usage above 90%
- AP memory usage above 85%
- Radio down
- VAP down
- Client RX rate too low
- Client TX rate too low
- Client RSSI too weak
- Interface operational status change
- No SNMP data received from the WLC
- No AP currently joined to the AC

Most item-level triggers depend on the controller being reachable and SNMP data being available, which helps reduce false positives during outages.

## Visualizations

The template also creates graphs for:

- AP online users
- AP CPU and memory usage
- Radio online users
- VAP client counts
- Interface traffic

## Value maps

The template includes value maps for:

- AP state
- VAP status
- Radio status
- Radio band
- Radio bandwidth
- STA band
- STA status
- SNMP interface status for `ifAdminStatus`
- SNMP interface status for `ifOperStatus`

## Requirements

- Zabbix 7.0 or newer
- SNMP access to the Huawei AC6000 controller
- The linked `ICMP Ping` template for reachability checks

## Import notes

- Template name: `Template Huawei AC6000 WLAN Discovery`
- Export format: native Zabbix YAML
- Main data source: SNMP

## Typical use case

Use this template on Huawei AC6000 wireless controllers to keep track of:

- Controller health
- AP registration and status
- Radio availability and utilization
- SSID/VAP health
- Wireless client experience
- Controller interface traffic and errors

This makes it suitable for operations teams that want one template to cover both controller-level and per-device WLAN visibility.
