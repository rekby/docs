---
editable: false
---
# Pricing policy for Managed Service for MySQL

{% include [currency-choice](../_includes/pricing/currency-choice.md) %}

## What goes into the cost of using Managed Service for MySQL {#rules}

The cost of Managed Service for MySQL usage is based on:

* Storage type and size (disk space).

* [The DB class](concepts/instance-types.md) selected for the cluster.

* How many DB hosts are in the clusters.

* Settings and number of backups.

* The amount of outgoing traffic.

{% include [pricing-gb-size](../_includes/pricing-gb-size.md) %}

### Use of DB hosts {#rules-hosts-uptime}

The cost is calculated for each hour of the host's operation in accordance with its class. The exact class characteristics are given in the section [#T](concepts/instance-types.md).

The minimum billing unit is one hour (for example, the cost of 1.5 hours of operation is the same as the cost of 2 hours of operation). You are not charged for time when the host MySQL is not performing its main functions.

### Disk space use {#rules-storage}

The following is charged:

* Storage allocated for DB clusters.
    * Storage on fast local disks (NVMe) can only be ordered for clusters with more than 3 hosts, in 100 GB increments.

* Space used by DB backups in excess of the storage specified for the cluster.

    * Backups are stored free of charge as long as the combined size of the DB and all backups is less than the selected storage volume.

    * The number of hosts in the cluster does not affect the size of the storage and, consequently, that of free backups.

The cost is specified for one month of use. The minimum billing unit is 1 GB per hour (for example, the cost of storing 1 GB for 1.5 hours is equal to the cost of storage for 2 hours).

## Pricing {#prices}

### Hosts {prices-hosts}

{% list tabs %}

- Per host per month
  
  | Host class | Rate for 1 hour, without VAT 
  | ----- | ----- 
  | **Intel Broadwell** | 
  | b1.nano (2 vCPU × 5%, 2 GB) | $0.009046 |
  | b1.micro (2 vCPU × 20%, 2 GB) | $0.015276 |
  | b1.medium (2 vCPU × 50%, 4 GB) | $0.028153
  | s1.nano (1 vCPU, 4 GB) | $0.034292
  | s1.micro (2 vCPU, 8 GB) | $0.063153
  | s1.small (4 vCPU, 16 GB) | $0.126323
  | s1.medium (8 vCPU, 32 GB) | $0.252646
  | s1.large (16 vCPU, 64 GB) | $0.505292
  | s1.xlarge (32 vCPU, 128 GB) | $1.010600
  | **Intel Cascade Lake** | 
  | b2.nano (2 vCPU × 5%, 2 GB) | $0.009046
  | b2.micro (2 vCPU × 20%, 2 GB) | $0.015276
  | b2.medium (2 vCPU × 50%, 4 GB) | $0.028153
  | s2.micro (2 vCPU, 8 GB) | $0.063153
  | s2.small (4 vCPU, 16 GB) | $0.126323
  | s2.medium (8 vCPU, 32 GB) | $0.252646
  | s2.large (12 vCPU, 48 GB) | $0.378984
  | s2.xlarge (16 vCPU, 64 GB) | $0.505292
  | s2.2xlarge (24 vCPU, 96 GB) | $0.757953
  | s2.3xlarge (32 vCPU, 128 GB) | $1.010600
  | s2.4xlarge (40 vCPU, 160 GB) | $1.263261
  | s2.5xlarge (48 vCPU, 192 GB) | $1.515907
  
- Prices in roubles
  
  | Host class | Rate for 1 hour, with VAT |
  | ----- | -----
  | **Intel Broadwell** | 
  | b1.nano (2 vCPU × 5%, 2 GB) | ₽0.7056 |
  | b1.micro (2 vCPU × 20%, 2 GB) | ₽1.1916 |
  | b1.medium (2 vCPU × 50%, 4 GB) | ₽2.1960 |
  | s1.nano (1 vCPU, 4 GB) | ₽2.6748 |
  | s1.micro (2 vCPU, 8 GB) | ₽4.9260 |
  | s1.small (4 vCPU, 16 GB) | ₽9.8532 |
  | s1.medium (8 vCPU, 32 GB) | ₽19.7064 |
  | s1.large (16 vCPU, 64 GB) | ₽39.4128 |
  | s1.xlarge (32 vCPU, 128 GB) | ₽78.8268 |
  | **Intel Cascade Lake** | 
  | b2.nano (2 vCPU × 5%, 2 GB) | ₽0.7056 |
  | b2.micro (2 vCPU × 20%, 2 GB) | ₽1.1916 |
  | b2.medium (2 vCPU × 50%, 4 GB) | ₽2.1960 |
  | s2.micro (2 vCPU, 8 GB) | ₽4.9260 |
  | s2.small (4 vCPU, 16 GB) | ₽9.8532 |
  | s2.medium (8 vCPU, 32 GB) | ₽19.7064 |
  | s2.large (12 vCPU, 48 GB) | ₽29.5608 |
  | s2.xlarge (16 vCPU, 64 GB) | ₽39.4128 |
  | s2.2xlarge (24 vCPU, 96 GB) | ₽59.1204 |
  | s2.3xlarge (32 vCPU, 128 GB) | ₽78.8268 |
  | s2.4xlarge (40 vCPU, 160 GB) | ₽98.5344 |
  | s2.5xlarge (48 vCPU, 192 GB) | ₽118.2408 |
  
{% endlist %}

### Storage and backups {#prices-storage}

{% list tabs %}

- Prices in USD
  | Service | Rate for 1 GB per month, without VAT |
  | ----- | ----- 
  | Standard network storage| $0.029334 |
  | Fast network storage| $0.104302 |
  | NVMe| $0.104302 |
  | Backups beyond the storage size| $0.032594 |
  
- Prices in roubles
  | Service | Rate for 1 GB per month, with VAT |
  | ----- | ----- 
  | Standard network storage| ₽2.2881 |
  | Fast network storage| ₽8.1356 |
  | NVMe| ₽8.1356 |
  | Backups beyond the storage size| ₽2.5424 |
  
{% endlist %}

### Outgoing traffic {#prices-traffic}

{% include notitle [pricing-egress-traffic](../_includes/pricing/pricing-egress-traffic.md) %}

