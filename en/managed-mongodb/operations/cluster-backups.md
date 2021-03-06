# How to manage backups

You can create backups and restore clusters from existing backups.

## Restoring clusters from backups {#restore}

When you restore a cluster from a backup, you create a new cluster with the data from the backup. If the folder has insufficient [resources](../concepts/limits.md) to create such a cluster, you will not be able to restore from the backup.

For a new cluster, you should set all the parameters that are required at creation, except for the cluster type (a MongoDB backup cannot be restored as a PostgreSQL cluster).

{% list tabs %}

- Management console
  
  1. Go to the folder page and click **Managed Service for MongoDB**.
  
  2. Click on the name of the cluster you need and select the tab **Backup copies**.
  
  3. Click ![image](../../_assets/dots.svg) for the required backup and then click **Restore cluster**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To restore a cluster from a backup:
  
  1. View the description of the CLI's restore cluster command MongoDB:
  
      ```
      $ yc managed-mongodb cluster restore --help
      ```
  
  2. Get a list of available backups for MongoDB clusters:
  
      ```
      $ yc managed-mongodb backup list
      
      +--------------------------+----------------------+----------------------+----------------------+
      |            ID            |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
      +--------------------------+----------------------+----------------------+----------------------+
      | c9qlk4v13uq79r9cgcku:... | 2018-11-02T10:08:38Z | c9qlk4v13uq79r9cgcku | 2018-11-02T10:08:37Z |
      | ...                                                                                           |                          |
      +--------------------------+----------------------+----------------------+----------------------+
      ```
  
  3. Request creation of a cluster from a backup:
  
      ```
      $ yc managed-mongodb cluster restore \
           --backup-id c9q287aqv5rf11isjeql:20181113T133617 \
           --name mynewmg \
           --environment=PRODUCTION \
           --network-name default \
           --host zone-id=ru-central1-c,subnet-id=b0rcctk2rvtr8efcch63 \
           --mongod-disk-size 20 \
           --mongod-disk-type network-nvme \
           --mongod-resource-preset s1.nano
      ```
  
      This results in a new MongoDB cluster with the following characteristics:
  
      * Named `mynewmg`.
  
      * In the `PRODUCTION` environment.
  
      * In the `default` network.
  
      * With a single host of the `s1.nano` in the `b0rcctk2rvtr8efcch63` subnet and the ` availability zoneru-central1-c`.
  
      * With the databases and users from the backup.
  
      * With SSD network storage of 20 GB.
  
{% endlist %}

## Creating backups {#create-backup}

{% list tabs %}

- Management console
  
  1. Go to the folder page and click **Managed Service for MongoDB**.
  
  2. Click on the name of the cluster you need and select the tab **Backup copies**.
  
  3. Click **Create a backup**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To create a cluster backup:
  
  1. See the description of the CLI's create backup command MongoDB:
  
      ```
      $ yc managed-mongodb cluster backup --help
      ```
  
  2. Request creation of a backup specifying the cluster name or ID:
  
      ```
      $ yc managed-mongodb cluster backup my-mg-cluster
      ```
  
      The cluster name and ID can be obtained with a [list of clusters](cluster-list.md#list-clusters).
  
{% endlist %}

## Getting a list of backups {#list-backups}

{% list tabs %}

- Management console
  
  1. Go to the folder page and click **Managed Service for MongoDB**.
  
  2. Click on the name of the cluster you need and select the tab **Backup copies**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To get a list of MongoDB cluster backups available in the default folder, run the command:
  
  ```
  $ yc managed-mongodb backup list
  
  +----------+----------------------+----------------------+----------------------+
  |    ID    |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
  +----------+----------------------+----------------------+----------------------+
  | c9qv4... | 2018-10-31T22:01:07Z | c9qv4ql6bd4hfo1cgc3o | 2018-10-31T22:01:03Z |
  | c9qpm... | 2018-10-31T22:01:04Z | c9qpm90p3pcg71jm7tqf | 2018-10-31T22:01:04Z |
  +----------+----------------------+----------------------+----------------------+
  ```
  
{% endlist %}

## Getting information about a backup {#get-backup}

{% list tabs %}

- Management console
  
  1. Go to the folder page and click **Managed Service for MongoDB**.
  
  2. Click on the name of the cluster you need and select the tab **Backup copies**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To get information about a MongoDB cluster backup, run the command:
  
  ```
  $ yc yc managed-mongodb backup get <backup ID>
  ```
  
  The backup ID can be obtained from a [list of backups](#list-backups).
  
{% endlist %}

