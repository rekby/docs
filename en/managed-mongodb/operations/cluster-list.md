# Information about existing clusters

You can request detailed information about each Managed Service for MongoDB cluster you created.

## Getting a list of DB clusters in a folder {#list-clusters}

{% list tabs %}

- Management console
  
  Go to the folder page and click **Managed Service for MongoDB**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To request a list of MongoDB clusters in the default folder, run the command:
  
  ```
  $ yc managed-postgresql cluster list
  
  +----------------------+------------+-----------------------------+--------+---------+
  |          ID          |    NAME    |         CREATED AT          | HEALTH | STATUS  |
  +----------------------+------------+-----------------------------+--------+---------+
  | c9wlk4v14uq79r9cgcku | mymg       | 2018-11-02T10:04:14.645214Z | ALIVE  | RUNNING |
  | ...                                                                                |
  +----------------------+------------+-----------------------------+--------+---------+
  ```
  
{% endlist %}

## Getting detailed information about a cluster {#get-cluster}

{% list tabs %}

- Management console
  
  1. Go to the folder page and click **Managed Service for MongoDB**.
  1. Click on the name of the cluster you need.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  To get information about a MongoDB cluster, run the command:
  
  ```
  $ yc managed-mongodb cluster get <cluster name or ID>
  ```
  
  The cluster name and ID can be requested with a [list of folder clusters](#list-clusters).
  
{% endlist %}

