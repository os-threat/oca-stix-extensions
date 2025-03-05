## dns-ext extension
Adds an extension to the [`network-traffic`](http://docs.oasis-open.org/cti/stix/v2.0/cs01/part4-cyber-observable-objects/stix-v2.0-cs01-part4-cyber-observable-objects.html#_Toc496716259) 
object to describe dns queries and answers. The key for this extension when used in the **extensions** dictionary **MUST** be dns-ext.

| property name | type | description |
|--|--|--|
| question.name_ref | `object-ref` | references the dns query domain name in question. must be of type `domain-name` |
|resolved_ip_refs|`list` of type `object-ref`| references ip addresses that were resolved by the answer. must be of type `ipv4-address` or `ipv6-address`|

In addition this object might contain any fields defined in the elastic ecs dns schema.
### Stix 2.0 Example:

    {
      "0":
      {
          "type": "network-traffic",
          "extensions":
          {
              "dns-ext":
              {
                  "question":
                  {
                      "name_ref": "1"
                  },
                  "resolved_ip_refs": ["2", "3"]
              }
          }
      },
      "1":
      {
          "type": "domain-name",
          "value": "domain.com"
      },
      "2":
      {
          "type": "ipv4-addr",
          "value": "9.9.9.9"
      },
      "3":
      {
          "type": "ipv6-addr",
          "value": "aaaa::bbbb:1111:2222:3333"
      }
    }

### Stix 2.1 Example
```json
[
  {
    "type": "network-traffic",
    "id": "network-traffic--a6728215-6c0a-4e2d-848f-76299ee4eca5",
    "spec_version": "2.1",
    "extensions": {
      "dns-ext": {
        "question": {
          "name_ref": "domain-name--0ba2599e-d2f1-5efd-87ad-77a272d6710c"
        },
        "resolved_ip_refs": [
          "ipv4-addr--33fb9fd7-3227-560d-90e5-2a2cb67ec010",
          "ipv6-addr--12de549b-20ef-5330-ae51-878b23250d8e"
        ]
      }
    }
  },
  {
    "type": "domain-name",
    "spec_version": "2.1",
    "id": "domain-name--0ba2599e-d2f1-5efd-87ad-77a272d6710c",
    "value": "domain.com"
  },
  {
    "type": "ipv4-addr",
    "spec_version": "2.1",
    "id": "ipv4-addr--33fb9fd7-3227-560d-90e5-2a2cb67ec010",
    "value": "9.9.9.9"
  },
  {
    "type": "ipv6-addr",
    "spec_version": "2.1",
    "id": "ipv6-addr--12de549b-20ef-5330-ae51-878b23250d8e",
    "value": "aaaa::bbbb:1111:2222:3333"
  }
]
```