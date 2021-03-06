# Access management

Yandex.Cloud users can only perform operations on resources that are allowed by the roles assigned to them. If a user doesn't have any roles assigned, almost all operations are forbidden.

To allow access to the Managed Service for MongoDB service resources (DB clusters and hosts, cluster backups, databases, and their users), assign the user the appropriate roles from the list below. At this time, a role can only be assigned to a parent resource (folder or cloud), and the roles are inherited by nested resources.

{% note info %}

For more information about role inheritance, see [#T](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) in the Yandex Resource Manager documentation.

{% endnote %}

## Assigning roles

To assign a role to a user:

{% include [grant-role-console](../../_includes/grant-role-console.md) %}

## Roles

The list below shows all roles that are considered when verifying access rights in the Managed Service for MongoDB service.

### Service roles

_Service roles_ are roles that allow access to the resources of a particular service.

{% include [cloud-roles](../../_includes/cloud-roles.md) %}

### Primitive roles

You can assign primitive roles to any resource in any service.

#### viewer

A user with the `viewer` can view information about resources. For example, they can view a list of hosts or obtain information about a DB cluster.

#### editor

A user with the `editor` can manage any resources. For example, they can create a DB cluster, and create or delete a host in a cluster.

In addition, the `editor` role includes all permissions of the `viewer` role.

#### admin

A user with the `admin` role can manage access rights to resources. For example, they can allow other users to create DB clusters or view information about them.

In addition, the `admin` role includes all permissions of the role of `editor`.

