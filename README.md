# bumpit

A simple command line [Semantic version](https://semver.org/) bumper.

Useful to add to your CI automation to bump your package version.

## Usage

```bash
$./bumpit.sh
usage: bumpit.sh [-Mmp] major.minor.patch

$./bumpit.sh -M 1.1.1
2.0.0

$./bumpit.sh -m 1.1.1
1.2.0

$./bumpit.sh -p 1.1.1
1.1.2

$./bumpit.sh -m 1.1.1-SNAPSHOT
1.2.0

./bumpit.sh -p 1.1.1-SNAPSHOT
1.1.2
```
