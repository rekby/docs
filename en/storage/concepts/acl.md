# Access control lists (ACLs)

Access control lists allow you to control access to buckets and objects.

Yandex.Cloud uses two independent mechanisms for managing access to Object Storage resources:

- Identity and Access Management ([IAM documentation](../../iam/concepts/index.md))
- ACL Object Storage

Object Storage creates ACLs for all objects and buckets. ACLs are empty by default. Users with the appropriate IAM rights can upload ACLs for Object Storage resources. Each ACL contains a list of users who are allowed to access objects and buckets and specifies user permissions. Permissions and users in the IAM and ACL may differ. To learn how Object Storage verifies access to resources, see  [Checking permissions](#permissions-check).

You can grant permission to Yandex.Cloud users, service accounts, and system groups.

To grant permission to a Yandex.Cloud user, you need to know their account ID. You can find the account ID:

- In the [IAM](https://console.cloud.yandex.com/iam) section of the management console.
- Using the [CLI or API](../../iam/operations/users/get.md).

To grant permission to a [service account](../../iam/concepts/users/service-accounts) you need to retrieve its ID in the Service accounts section of the management console.

To grant permission to a system group, you need to know its URI. For more information, see [System groups](#system_groups).

Object Storage supports [predefined ACLs](#predefined_acls), which contain common permission sets.

The ACL structure can be viewed in the [ACL XML schema](../s3/api-ref/acl/xmlscheme.md).

Object Storage supports operations for uploading and downloading ACLs. No operation is available to delete ACLs. To remove all access permissions, upload an empty ACL. Object Storage creates an empty ACL for each new object or bucket by default.

{% note info %}

ACLs uploaded for objects are applied immediately. ACLs uploaded for buckets and access permissions updated in the IAM service apply after a delay. For more information about delays, see [IAM documentation](../../iam/concepts/access-control/index.md).

{% endnote %}

## Checking permissions {#permissions-check}

Yandex.Cloud uses two mechanisms for managing access to Object Storage resources:

- Identity and Access Management
- ACL

When receiving a request to a bucket or object, Object Storage checks access permissions with both mechanisms. If the required access is granted from either method, Object Storage executes the request.

Permissions granted to a bucket apply to all of the objects it contains.  You can extend user permissions to individual objects by adding them to the relevant objects' ACL.

## Permission types

Permissions correspond to user roles in Identity and Access Management.

| Permission | IAM role | Description |
| -------------------- | ------------ | -------- |
| `READ` | `viewer` | For buckets: permission to retrieve a list of objects in the bucket, read various bucket settings (lifecycle, CORS, static hosting), and read all objects in the bucket.<br/><br/>For objects: read permission. |
| `WRITE` | `editor` | For buckets: permission to write objects to the bucket.<br/>It must be used along with `READ`. You cannot specify `WRITE` separately.<br/><br/>For objects: this permission is meaningless, as permission is checked for the bucket when writing an object. |
| `FULL_CONTROL` | `admin` | Full access to objects and buckets. |
| `READ_ACP` | `viewer` | ACL read permission. For objects only. |
| `WRITE_ACP` | `editor` | ACL write permission. For objects only. |

{% note info %}

If you specify `WRITE` permission but not `READ` when making an ACL, Object Storage will return code `501 Not Implemented`.

{% endnote %}

## Predefined ACLs {#predefined_acls}

| ACL | Description |
| ---- | --------- |
| `private`<br/>`bucket-owner-full-control` | Cloud users are granted permissions according to their roles in IAM. |
| `public-read` | The system `AllUsers` group has `READ` permission. |
| `public-read-write` | The system `AllUsers` group has `READ` and `WRITE` permissions. |
| `authenticated-read` | The system `AuthenticatedUsers` group has `READ` permission. |

Predefined ACLs can be applied to both objects and buckets. When applied to an object, the `public-read-write` ACL is the same as `public-read`.

## System groups {#system_groups}

### AllUsers

Includes all internet users.

Permission for `AllUsers` looks like this:

```
<Grantee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="Group">
    <URI>http://acs.amazonaws.com/groups/global/AllUsers</URI>
</Grantee>
```

### AuthenticatedUsers

Includes all Yandex.Cloud users.

Permission for `AuthenticatedUsers` looks like this:

```
<Grantee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="Group">
    <URI>http://acs.amazonaws.com/groups/global/AuthenticatedUsers</URI>
</Grantee>
```

