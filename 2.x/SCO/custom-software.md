## software object with custom attributes

Specifies custom atributes for the [`software`](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_7rkyhtkdthok) object to describe commonly used descriptors for a software or file.

| property name | type | description |
|--|--|--|
| x_product | `string` | Specifies the internal product name of the file, provided at compile-time. e.g., Microsoft® Windows® Operating System |
| x_description | `string` | Specifies the internal description of the file, provided at compile-time. e.g., Paint |

### Stix 2.0 Example:

    {
        "0": {
            "type": "software",
            "version": "10.0.17763.1 (WinBuild.160101.0800)",
            "x_product": "Microsoft\u00ae Windows\u00ae Operating System",
            "x_description": "Host Process for Windows Services",
            "vendor": "Microsoft Corporation",
            "name": "svchost.exe"
        }
    }

### Stix 2.1 Example
```json
[
  {
    "type": "software",
    "spec_version": "2.1",
    "id": "software--0c2fe928-11e8-5d42-9183-104e60e3f9a6",
    "version": "10.0.17763.1 (WinBuild.160101.0800)",
    "x_product": "Microsoft\u00ae Windows\u00ae Operating System",
    "x_description": "Host Process for Windows Services",
    "vendor": "Microsoft Corporation",
    "name": "svchost.exe"
  }
]
```