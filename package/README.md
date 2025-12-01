# aux4/system-installer-apt

aux4 system installer for apt

This package provides a small aux4 wrapper around the apt package manager so you can manage Debian/Ubuntu (and other APT-based) packages via aux4 commands. It exposes install and uninstall actions and maps both the `apt` and `linux` top-level names to the same functionality so it fits naturally into aux4 pkger/system workflows.

Main use cases:
- Quickly install a package from apt inside aux4 workflows and scripts.
- Remove a package using the same simple command path.
- Use as the apt-backed system installer when authoring aux4 packages that list apt as a system installer.

This package is targeted at Linux systems and integrates with the aux4 package manager (it depends on aux4/pkger being available).

## Installation

```bash
aux4 aux4 pkger install aux4/system-installer-apt
```

## Quick Start

Install a package named curl:

```bash
aux4 aux4 pkger system apt install curl
```

This runs apt install -y curl on the host. Run the command as root or prefix with sudo so apt has permission to install packages.

## Install a package

Use this for the common case: installing a single apt package by name.

The command is available at [aux4 aux4 pkger system apt install](./commands/aux4/pkger/system/apt/install).

```bash
aux4 aux4 pkger system apt install <package>
```

Replace <package> with the package name (for example, curl). The command expands to `apt install -y ${package}` and will install the package non-interactively.

## Uninstall a package

Remove a package with the corresponding uninstall action. This maps to `apt remove -y ${package}`.

The command is available at [aux4 aux4 pkger system apt uninstall](./commands/aux4/pkger/system/apt/uninstall).

```bash
aux4 aux4 pkger system apt uninstall <package>
```

Run as root or with sudo so apt can remove packages.

## Using the linux alias

This package exposes the same functionality under the `linux` name (an alias for `apt`) so you can invoke it as:

```bash
aux4 aux4 pkger system linux install curl
```

This is equivalent to `aux4 aux4 pkger system apt install curl` and exists for convenience in workflows that reference "linux" as the system type.

## Examples

### Install curl (minimal)

Install curl non-interactively:

```bash
aux4 aux4 pkger system apt install curl
```

This executes `apt install -y curl`. Use root or sudo to avoid permission errors.

### Remove curl

Uninstall curl:

```bash
aux4 aux4 pkger system apt uninstall curl
```

This executes `apt remove -y curl` and will remove the package non-interactively.

### Use the linux alias

Install wget using the alias:

```bash
aux4 aux4 pkger system linux install wget
```

This is identical to calling the `apt` command and may read more clearly in workflows that use `linux` as the system installer name.

## Requirements

- Platform: linux
- aux4/pkger must be available (this package is intended to be used via aux4's package manager)

## License

This package is licensed under the Apache License 2.0.

See [LICENSE](./license) for details.
