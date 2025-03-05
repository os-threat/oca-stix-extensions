## process object with custom attributes

Specifies custom atributes for the [`process`](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_hpppnm86a1jm) object to describe commonly used descriptors for a process.

| property name | type | description |
|--|--|--|
| x_window_title | `string` | Specifies the title of a process. This is some times the same as process name. Can also be different: for example a browser setting its title to the web page currently opened. |
| x_thread_id | `integer` | Specifies the id of the thread related to the process. For a multi-threaded process, this specifies the id of the first thread initialized by the process. |
| x_exit_code | `integer` | Specifies the exit code of a process. Present if this is a terminaton event. |
| x_uptime | `integer` | Specifies the amount of time in seconds a process has been up. |
| x_unique_id | `string` | Specifies globally unique identifier for a process, commonly used to mitigate PID reuse and to identify a specific process over time, across multiple monitored hosts.  For example - process-generated UUID, Sysmon Process GUIDs, or a hash of some uniquely identifying components of a process. |
| x_tags | `list` of type `string` | Specifies the list of keywords used to tag an event. |

### Stix 2.0 Example:

    {
        "0": {
            "type": "process",
            "name": "services.exe",
            "pid": 1068,
            "x_unique_id": "{8dfc401c-1ef5-6175-0b00-000000001b00}",
            "image_ref": "2",
            "command_line": "C:\\Windows\\system32\\services.exe"
        },
        "1": {
            "type": "process",
            "parent_ref": "0",
            "name": "svchost.exe",
            "pid": 2244,
            "cwd": "C:\\Windows\\system32\\",
            "x_unique_id": "{8dfc401c-1ef7-6175-2900-000000001b00}",
            "x_thread_id": "4242",
            "command_line": "C:\\Windows\\system32\\svchost.exe -k netsvcs -p -s Schedule",
            "x_tags": [
                "beats_input_codec_plain_applied"
            ]
        },
        "2": {
            "type": "file",
            "name": "services.exe",
            "parent_directory_ref": "3"
        },
        "3": {
            "type": "directory",
            "path": "C:\\Windows\\System32"
        }
    }

### Stix 2.1 Examples:
```json
[
  {
    "type": "process",
    "id": "process--00abedb4-aa42-466c-9c01-fed23315a9b7",
    "spec_version": "2.1",
    "name": "services.exe",
    "pid": 1068,
    "x_unique_id": "{8dfc401c-1ef5-6175-0b00-000000001b00}",
    "image_ref": "file--79902ec1-126f-5385-8d02-841c56b7a926",
    "command_line": "C:\\Windows\\system32\\services.exe"
  },
  {
    "type": "process",
    "id": "process--d2062cd4-a6a5-498d-8ec4-87a2da23006f",
    "spec_version": "2.1",
    "parent_ref": "process--00abedb4-aa42-466c-9c01-fed23315a9b7",
    "name": "svchost.exe",
    "pid": 2244,
    "cwd": "C:\\Windows\\system32\\",
    "x_unique_id": "{8dfc401c-1ef7-6175-2900-000000001b00}",
    "x_thread_id": "4242",
    "command_line": "C:\\Windows\\system32\\svchost.exe -k netsvcs -p -s Schedule",
    "x_tags": [
      "beats_input_codec_plain_applied"
    ]
  },
  {
    "type": "file",
    "id": "file--79902ec1-126f-5385-8d02-841c56b7a926",
    "spec_version": "2.1",
    "name": "services.exe",
    "parent_directory_ref": "directory--f9fd432b-f72d-5bf4-8433-273d5bc5e465"
  },
  {
    "type": "directory",
    "id": "directory--f9fd432b-f72d-5bf4-8433-273d5bc5e465",
    "spec_version": "2.1",
    "path": "C:\\Windows\\System32"
  }
]
```