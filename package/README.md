# system-installer-apt

The [aux4 system installer](/r/public/packages/aux4/pkger/commands/aux4/pkger/system) is used to manage packages by another package system. It is used to install and uninstall system packages.

```json
{
  "scope": "<scope>",
  "name": "<name>",
  "version": "<version>",
  ...
  "system": [
    ["apt:jq"]
  ],
  "profiles": [
    ...
  ]
}
```

In this case when the *aux4 package is installed*, it will install the `jq` package using the `apt` package manager.

```bash
> apt install jq
```

In the same way, when the *aux4 package is uninstalled*, it will uninstall `jq` package using the `apt` package manager (only if they are not used by another aux4 package).

```bash
> apt uninstall jq
```

Check out the [aux4 pkger system apt](commands/aux4/pkger/system/apt) command for more information.

