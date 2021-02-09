# solc-select
A script to quickly switch between Solidity compiler versions.

It is becoming increasingly hard to run older versions of `solc`,
particularly on macOS since there are no official binary releases.
Versions prior to 0.5.0 no longer compile on macOS and are not
maintained. This is a problem because older Ethereum contracts no
longer compile on modern versions of Solidity. `solc-select` is a
utility that allows one to run _any_ legacy version of Solidity simply
by setting an environment variable.

## Quickstart

```pip3 install solc-select```

## Usage

The desired version of `solc` can be set with the `use` command. By default, the latest version is used.

```
$ solc --version
solc, the solidity compiler commandline interface
Version: 0.5.2+commit.1df8f40c.Linux.g++
$ solc use 0.4.24
solc, the solidity compiler commandline interface
Version: 0.4.24+commit.e67f0147.Linux.g++
```


In special scenarios the current version can also be overwritten with the `SOLC_VERSION` environment variable.

```
$ solc --version
solc, the solidity compiler commandline interface
Version: 0.4.24+commit.e67f0147.Linux.g++
$ SOLC_VERSION=0.5.2 solc --version
solc, the solidity compiler commandline interface
Version: 0.5.2+commit.1df8f40c.Linux.g++
```


You can list all available versions with the special `--versions` argument:
```
$ solc --versions
0.4.11
0.4.12
0.4.13
0.4.14
0.4.15
0.4.16
0.4.17
0.4.18
0.4.19
0.4.20
0.4.21
0.4.22
0.4.23
0.4.24
0.4.25
0.5.0
0.5.1
0.5.2
0.5.3
0.5.4
0.5.5
nightly
```

## Upgrading

Once installed, simply run
```
solc --upgrade
```
to automatically upgrade `solc-select`. This will automatically pull the latest Docker image (or repo source, depending on your OS) and upgrade the local `solc` script, if necessary. The [DockerHub image for `solc-select`](https://hub.docker.com/r/trailofbits/solc-select) will automatically update every time Solidity is updated, which will typically be nightly.

## Installation from Source on OS X

```
$ git clone https://github.com/trailofbits/solc-select.git
$ cd solc-select
$ docker build -t trailofbits/solc-select:latest .
$ bin/solc --install
```

## Experimental solc-select

The experimental version of `solc-select` is a Python-based script without any
additional dependencies. Both macOS and Linux solc binaries are downloaded from
https://binaries.soliditylang.org/ and macOS binaries run natively. Some
features are still missing, like version range installation or nightly builds.

Try it out:
```
git clone https://github.com/crytic/solc-select ~/.solc-select
export PATH=~/.solc-select/experimental/bin:$PATH
solc-select --help
```

## Getting Help

Feel free to stop by our [Slack channel](https://empirehacking.slack.com/) for help on using or extending `solc-select`.

## License

`solc-select` is licensed and distributed under the [AGPLv3](LICENSE) license. [Contact us](mailto:opensource@trailofbits.com) if you’re looking for an exception to the terms.
