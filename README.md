# DDEV TYPO3 Extension Setup

This repository provides a boilerplate for TYPO3 extensions with DDEV integration.

## Features

- Multi-TYPO3 version support (11.5, 12.4, 13.4)
- Static code analysis within composer scripts for local development and CI
- TER release github workflow

## Setup

1. Copy the entire `.ddev` folder to your project's root
2. Search and replace in all files
    - search for `extension_key` and `extension-key` to replace them with your **extension key**
3. Adjust the `composer.json` regarding the package name, vendor and autoload section

## Usage

```
$ ddev start
```

Install TYPO3 environments

```
$ ddev install all
```


## Honoration

This repository is partly inspired by the following packages and adjusted to my own needs. 

- https://github.com/a-r-m-i-n/ddev-for-typo3-extensions
- https://github.com/sourcebroker/t3api