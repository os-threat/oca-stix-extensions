## user-account object with custom attributes

Specifies custom atributes for the [`user-account`](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_azo70vgj1vm2) object to describe commonly used descriptors for a user account.

| property name | type | description |
|--|--|--|
| x_domain | `string` | Specifies the internal product name of the file, provided at compile-time. e.g., Microsoft® Windows® Operating System |
| x_hash | `string` | Specifies the unique user hash to correlate information for a user in anonymized form. It is useful if user.id or user.name contain confidential information and cannot be used. |
| x_group | `dictionary` | Specifies the groups that are relevant to the event. Each dictionary key SHOULD come from the user group vocabulary.|

### User group vocabulary
| value | type | description |
|--|--|--|
| domain | `string` | Specifies the name of the directory the group is a member of. e.g., an LDAP or Active Directory domain name|
| gid | `integer` | Specifies the unique identifier for the group on the system/platform |
| name | `string` | Specifies the name of the group |

### Stix 2.0 Example:

    {
        "0": {
            "type": "user-account",
            "x_domain": "NT AUTHORITY",
            "user_id": "SYSTEM",
            "account_login": "SYSTEM",
            "x_group.gid": "515",
            "x_group.name": "Domain local group",
            "x_group.domain": "internal.company.com"
        }
    }

### Stix 2.1 Example:
```json
[
  {
    "type": "user-account",
    "id": "user-account--1048a0ef-2c4b-57b4-b5f1-21a1043c4aff",
    "spec_version": "2.1",
    "x_domain": "NT AUTHORITY",
    "user_id": "SYSTEM",
    "account_login": "SYSTEM",
    "x_group.gid": "515",
    "x_group.name": "Domain local group",
    "x_group.domain": "internal.company.com"
  }
]
```