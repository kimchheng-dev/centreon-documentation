---
id: applications-antivirus-clamav-ssh
title: Antivirus ClamAV
---

## Overview

*Describe quickly what the brand the associated devices are*

The Centreon Plugin Pack *Antivirus ClamAV* aims to collect...

## Pack assets

### Monitored objects

* Plugin Target 1 

* Plugin Target 2

* ...

### Monitored metrics

<!--DOCUSAURUS_CODE_TABS-->

<!--Update-Status-->

| Metric name    | Description |
|:---------------|:------------|
| engine-status  |             |
| maindb-status  |             |
| dailydb-status |             |
| daily          |             |
| main           |             |

<!--END_DOCUSAURUS_CODE_TABS-->

## Prerequisites

*Specify prerequisites that are relevant. You may want to just provide a link to
the manufacturer official documentation BUT you should try to be as complete as
possible here as it will save time to everybody*

## Setup

<!--DOCUSAURUS_CODE_TABS-->

<!--Online IMP Licence & IT-100 Editions-->

1. Install the Centreon Plugin package on every Centreon poller expected to monitor *TO CHANGE* ressources:

```bash
yum install centreon-plugin-Applications-Clamav-Ssh
```

2. On the Centreon Web interface, install the *Antivirus ClamAV* Centreon Plugin Pack on the "Configuration > Plugin Packs" page

<!--Offline IMP License-->

1. Install the Centreon Plugin package on every Centreon poller expected to monitor *TO CHANGE* ressources:

```bash
yum install centreon-plugin-Applications-Clamav-Ssh
```

2. Install the *Antivirus ClamAV* Centreon Plugin Pack RPM on the Centreon Central server:

 ```bash
yum install centreon-pack-applications-antivirus-clamav-ssh
```

3. On the Centreon Web interface, install the *Antivirus ClamAV* Centreon Plugin Pack on the "Configuration > Plugin Packs" page

<!--END_DOCUSAURUS_CODE_TABS-->

## Configuration

### Host

 * Log into Centreon and add a new Host through "Configuration > Hosts".
 * Fill the "Name", "Alias" & "IP Address / DNS" fields according to your *TO CHANGE* Server settings
 * Select the *Applications-Antivirus-Clamav-Ssh-custom* template to apply to the Host
 * Once the template applied, some Macros marked as 'Mandatory' hereafter have to be configured.
 

| Mandatory | Name         | Description                                                                        |
|:----------|:-------------|:-----------------------------------------------------------------------------------|
|           | EXTRAOPTIONS | Any extra option you may want to add to every command\_line (eg. a --verbose flag) |

## How to check in the CLI that the configuration is OK and what are the main options for ? 

 Once the plugin installed, log into your Centreon Poller CLI using the 
 *centreon-engine* user account and test the Plugin by running the following 
 command:

 ```bash
 /usr/lib/centreon/plugins//centreon_clamav_ssh.pl  \
    --plugin=apps::antivirus::clamav::local::plugin  \
    --mode=update-status  \
    --hostname=10.0.0.1  \
    --remote   \
    --warning-engine-status=''  \
    --critical-engine-status='' \
    --warning-maindb-status=''  \
    --critical-maindb-status='%{last_maindb_version} ne %{current_maindb_version}' \
    --warning-dailydb-status=''  \
    --critical-dailydb-status='%{last_dailydb_version} ne %{current_dailydb_version} || %{current_dailydb_timediff} > 432000'
 ```

 Expected command output is shown below:

 ```bash
OK : .... | 
 ```

  This command would trigger a WARNING alarm if *WHAT* is reported as (--warning-vault-availability-percentage) and a CRITICAL alarm if less than 50% (--critical-vault-availability-percentage='50:').

 All available options for a given mode can be displayed by adding the 
```--help``` parameter to the command:

 ```bash
 /usr/lib/centreon/plugins//centreon_clamav_ssh.pl  \
    --plugin=apps::antivirus::clamav::local::plugin  \
    --help
 ```

 All available options for a given mode can be displayed by adding the 
```--list-mode``` parameter to the command:

 ```bash
 /usr/lib/centreon/plugins//centreon_clamav_ssh.pl  \
    --plugin=apps::antivirus::clamav::local::plugin  \
    --list-mode
 ```

 ### Troubleshooting
 
 #### ```Error message```
 ...... 
