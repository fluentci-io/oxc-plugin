# Oxc Plugin

[![fluentci pipeline](https://shield.fluentci.io/x/oxc)](https://pkg.fluentci.io/oxc)
[![ci](https://github.com/fluentci-io/oxc-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/oxc-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with [oxc tools](https://github.com/oxc-project/oxc).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm oxc setup
```

## Functions

| Name   | Description                                                       |
| ------ | ----------------------------------------------------------------- |
| setup  | Installs oxc tools                                                |
| lint   | Lints the project using oxlint                                    |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.1.9"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/oxc@v0.1.0?wasm=1", "setup", vec![])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: oxc
    args: |
      setup
- name: Show oxlint version
  run: |
    export PATH=${HOME}/.bun/bin:${PATH}
    type oxlint
    oxlint --version
```
