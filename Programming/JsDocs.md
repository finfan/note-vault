
#jsdocs

command to use
```cmd
npx jsdoc <path to javascript file>
```
# list usage of the command npx jsdoc

The `npx jsdoc` command generates API documentation from JavaScript source files with JSDoc comments. Here are the primary usage patterns and options:
## Basic Usage
 
```bash

npx jsdoc yourfile.js

npx jsdoc file1.js file2.js folder/

npx jsdoc src/ --recurse

```
## Common Command Line Options
**Output Control:**
```

- `-d <path>` or `--destination <path>` - Specify output directory (defaults to `./out`)

```

  ```

- `-c <path>` or `--configure <path>` - Use configuration file

```

```

- `-t <path>` or `--template <path>` - Specify custom template

```

**File Processing:**
- `-r` or `--recurse` - Process subdirectories recursively

```

- `-e <encoding>` or `--encoding <encoding>` - File encoding (defaults to utf8)

```

- `-P` or `--package` - Include package.json information

- `-R` or `--readme` - Include README file in documentation

**Content Options:**
- `-p` or `--private` - Include private symbols marked with `@private`

```

- `-a <value>` or `--access <value>` - Filter by access level (`private`, `protected`, `public`, `undefined`, or `all`)

```

**Debugging and Testing:**
- `--debug` - Enable debug logging

- `--verbose` - Detailed console output

- `-X` or `--explain` - Output all doclets as JSON

- `-T` or `--test` - Run JSDoc test suite

## Usage Examples
**Generate docs with custom output directory:**

```bash

npx jsdoc src/ -d docs/ --recurse

```
 

**Use configuration file:**
```bash

npx jsdoc -c jsdoc.conf.json

```

**Include private methods and use custom template:**
```bash

npx jsdoc src/ --private --template ./custom-template

```
 
**Generate docs with README and package info:**
```bash

npx jsdoc src/ --recurse --readme README.md --package package.json

```

**Debug mode with verbose output:**
```bash

npx jsdoc src/ --debug --verbose

```

## Configuration File Usage

Create a `jsdoc.conf.json` file for complex setups:

```bash

npx jsdoc -c jsdoc.conf.json

```

The configuration file typically includes source directories, output destination, plugins, and template settings.[^1][^5][^6]

[^1]: https://jsdoc.app/about-commandline
[^2]: https://jsdoc.app
[^3]: https://stackoverflow.com/questions/33948829/how-do-i-use-jsdoc-on-windows
[^4]: https://jsdoc.app/about-getting-started
[^5]: https://www.geeksforgeeks.org/javascript/introduction-to-jsdoc/
[^6]: https://www.npmjs.com/package/jsdoc
[^7]: https://precodes.hashnode.dev/jsdoc-the-ultimate-guide-to-documenting-your-javascript-code
[^8]: https://dev.to/alisamir/a-comprehensive-guide-to-jsdoc-3meb
[^9]: https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html