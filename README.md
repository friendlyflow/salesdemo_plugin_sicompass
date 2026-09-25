# salesdemo-plugin-sicompass

*The Sicompass sales demo: configure a product by walking its tree.*

This plugin is part of [Sicompass](https://github.com/friendlyflow/sicompass), a
keyboard-first, accessibility-first way to use your entire computer.

It shows a product configuration tree, here an air handling unit. The parts a
product always has appear directly. The optional parts are listed under "Add
element:", and pressing one adds it to the configuration, with its own options.
Press d at the top to see the unit's diagram. A configuration can be saved to a
file and opened again.

It runs in the Sicompass sandbox and asks for no access at all: it reads only
the files it ships with.

## Install

In Sicompass, open store, then programs, and press Enter on install next to
sales demo. The Store checks the release's signature before installing it, and
keeps it up to date.

To install a build of your own instead, copy `plugin.json`, `plugin.wasm`,
`assets/` and `locales/` into a folder named `salesdemo` in the Sicompass
plugins folder (`~/.config/sicompass/plugins/` on Linux) and restart Sicompass.

## Building from source

```bash
nix develop          # the toolchain, with the wasm32-wasip2 target
cargo test           # the tree logic, natively
cargo build --release --target wasm32-wasip2
cp target/wasm32-wasip2/release/salesdemo_plugin.wasm plugin.wasm
```

`./scripts/release-plugin.sh --dry-run` does the build, checks the component
against `plugin.json`, and signs and verifies it with a throwaway key, the way
a release is made.

## Related repositories

- [sicompass](https://github.com/friendlyflow/sicompass), the application
- [sicompass-plugin-sdk](https://github.com/friendlyflow/sicompass-plugin-sdk),
  the SDK and the WASM plugin kit

## Community

Join the conversation on
[Discord](https://discord.com/channels/1464152138753249313/1464152139231137894).

## License

#### Open source license

If you are creating an open source application under a license compatible with
the GNU GPL license v3, you may use this project under the terms of the GPLv3.
See [LICENSE](LICENSE).

## Contributing

Contributions are welcome. Whether it is code, documentation, or feedback, your
input helps make computing more accessible for everyone.
