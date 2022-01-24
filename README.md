# bump

A simple command line [Semantic version](https://semver.org/) bumper.

Useful to add to your CI automation to bump your package version.

## Usage

```bash
$./bump
usage: bump [-Mmp] major.minor.patch

$./bump -M 1.1.1
2.0.0

$./bump -m 1.1.1
1.2.0

$./bump -p 1.1.1
1.1.2

$./bump -m 1.1.1-SNAPSHOT
1.2.0

./bump -p 1.1.1-SNAPSHOT
1.1.2
```
