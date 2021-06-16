# xscad contept rfc

### Library structure
xscad require the following structure:
```
- [📁] xscad (generated folder, xscad will place dependencies here)
- 📁 asset
    - 📄 clock.svg
- 📁 script
    - 🔨 bolt.py
- 📄 myfile.scad
- 📄 file1.scad
- 📄 file2.scad
- ⚙️ xscad.toml
```

`script` folder - place to store all python scripts
`scad.toml` - main package configuration file

### What is not supported and most likely would not change
- Wildcard versions (e.g. `1.*`) are not supported. Only fully specified notation is supported (e.g. `1.0.1`)
- Dependencies deduplication is not supported for example, if crate `A` depends on `B` and `C`, and `B` also depends on `C`,
  then xscad folder structure for `A` will like like this:
  ```
  - 📁 xscad
      - 📁 B
          - 📁 C
      - 📁 C
  ```
  This is done because of OpenSCAD search path limitations

### xscad.toml structure
TODO

### xscad commands
- `xscad build` - resolve all dependencies, execute stripts (if scripts execution enabled)
- `xscad publish` - validate package, pack it to `.xscad` format and publish to the main
  repository. xscad does not have its own servers yet, so to publish package, you need to register
  free account for cloudsmith.io and generate API key for publishing
- `xscad search <package_name> [--version=<version>]` - find package in registry
- `xscad init` - create new xscad project in the current directory

### working with xscad project
Just execute xscad build and wait. Usually 
