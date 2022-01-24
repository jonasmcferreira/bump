# bumpit

A simple command line [Semantic version](https://semver.org/) bumper.

Useful to add to your CI automation to bump your package version.

## Usage

```bash
$./bumpit
usage: bumpit [-Mmp] major.minor.patch

$./bumpit -M 1.1.1
2.0.0

$./bumpit -m 1.1.1
1.2.0

$./bumpit -p 1.1.1
1.1.2

$./bumpit -m 1.1.1-SNAPSHOT
1.2.0

./bumpit -p 1.1.1-SNAPSHOT
1.1.2
```
