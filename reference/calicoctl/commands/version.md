---
title: calicoctl version
canonical_url: 'https://docs.projectcalico.org/v3.2/reference/calicoctl/commands/version'
---

This section describes the `calicoctl version` command.

Read the [calicoctl Overview]({{site.baseurl}}/reference/calicoctl/) 
for a full list of calicoctl commands.

## Displaying the help text for 'calicoctl version' commands

Run `calicoctl version --help` to display the following help menu for the 
commands.

```
Usage:
  calicoctl version [--config=<CONFIG>]

Options:
  -h --help             Show this screen.
  -c --config=<CONFIG>  Path to the file containing connection configuration in
                        YAML or JSON format.
                        [default: /etc/calico/calicoctl.cfg]

Description:
  Display the version of calicoctl.
```

### Example

Use `calicoctl version` to obtain the following data.

{% include calicoctl-version.md %}

\* To obtain these values, you must configure `calicoctl` 
   [to connect to your datastore](/usage/calicoctl/configure/).


## See also

-  [calicoctl configuration]({{site.baseurl}}/reference/calicoctl/setup) 
   for details on configuring `calicoctl` to access the {{site.prodname}} datastore.
