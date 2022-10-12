---
id: hardware-sensors-hwgste-snmp
title: HWg-STE Sensor
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


## Pack Assets

### Templates

The Centreon Plugin Pack **HWg-STE Sensor** brings a host template:

* HW-Sensors-HWgSTE-SNMP-custom

It brings the following service template:

| Service Alias  | Service Template                     | Service Description            | Default |
|:---------------|:-------------------------------------|:-------------------------------|:--------|
| Sensors-Global | HW-Sensor-HWgSTE-Sensors-Global-SNMP | Check all sensors of equipment | X       |

### Collected metrics & status

<Tabs groupId="sync">
<TabItem value="Sensors-Global" label="Sensors-Global">

Could not retrieve metrics

</TabItem>
</Tabs>

## Prerequisites

### SNMP Configuration

To use this pack, the SNMP service must be properly configured on your **HWg-STE Sensor**
server. Please refer to the official documentation from HWg-STE:
* [HWg-STE](https://www.hw-group.com/revision-overview/manuals)

### Network flow

The target server must be reachable from the Centreon poller on the UDP/161
SNMP port.

## Setup

<Tabs groupId="sync">
<TabItem value="Online License" label="Online License">

1. Install the plugin package on every Centreon poller expected to monitor **HWg-STE Sensor** resources:

```bash
yum install centreon-plugin-Hardware-Sensors-Hwgste-Snmp
```

2. On the Centreon web interface, on page **Configuration > Plugin Packs**, install the **HWg-STE Sensor** Centreon Plugin Pack.

</TabItem>
<TabItem value="Offline License" label="Offline License">

1. Install the plugin package on every Centreon poller expected to monitor **HWg-STE Sensor** resources:

```bash
yum install centreon-plugin-Hardware-Sensors-Hwgste-Snmp
```

2. Install the **HWg-STE Sensor** Centreon Plugin Pack RPM on the Centreon central server:

```bash
yum install centreon-pack-hardware-sensors-hwgste-snmp
```

3. On the Centreon web interface, on page **Configuration > Plugin Packs**, install the **HWg-STE Sensor** Centreon Plugin Pack.

</TabItem>
</Tabs>

## Configuration

### Host

* Log into Centreon and add a new host through **Configuration > Hosts**.
* Fill the **Name**, **Alias** & **IP Address/DNS** fields according to your **HWg-STE Sensor** server settings.
* Apply the **HW-Sensors-HWgSTE-SNMP-custom** template to the host.

> When using SNMP v3, use the SNMPEXTRAOPTIONS Macro to add specific authentication parameters 
> More information in the [Troubleshooting SNMP](../getting-started/how-to-guides/troubleshooting-plugins.md#snmpv3-options-mapping) section.

| Mandatory   | Macro            | Description                                  |
|:------------|:-----------------|:---------------------------------------------|
|             | SNMPEXTRAOPTIONS | Configure your own SNMPv3 credentials combo  |

## How to check in the CLI that the configuration is OK and what are the main options for?

Once the plugin is installed, log into your Centreon poller's CLI using the
**centreon-engine** user account (`su - centreon-engine`) and test the plugin by
running the following command:

```bash
/usr/lib/centreon/plugins//centreon_hwgste.pl \
    --plugin=hardware::sensors::hwgste::snmp::plugin \
    --mode=sensors \
    --hostname=10.0.0.1 \
    --snmp-community='my-snmp-community' \
    --snmp-version='2c' \
    --component='.*' \
    --warning='' \
    --critical='' \
    --verbose \
    --use-new-perfdata
```

The expected command output is shown below:

```bash
OK: | 
```

All available options for a given mode can be displayed by adding the
`--help` parameter to the command:

```bash
/usr/lib/centreon/plugins//centreon_hwgste.pl \
    --plugin=hardware::sensors::hwgste::snmp::plugin \
    --mode=sensors \
    --help
```

All available modes can be displayed by adding the `--list-mode` parameter to
the command:

```bash
/usr/lib/centreon/plugins//centreon_hwgste.pl \
    --plugin=hardware::sensors::hwgste::snmp::plugin \
    --list-mode
```

### Troubleshooting

Please find the [troubleshooting documentation](../getting-started/how-to-guides/troubleshooting-plugins.md)
for Centreon Plugins typical issues.