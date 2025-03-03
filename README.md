# DDEV TYPO3 Extension Setup

This repository provides a boilerplate for TYPO3 extensions with DDEV integration.

## Features

- Local Multi-TYPO3 version DDEV instance support (11.5, 12.4, 13.4)
- Static code analysis within composer scripts for local development and CI
- TER release github workflow

## Setup

1. Copy the `.ddev`, `.github` folders and `composer.json`, `.gitignore` to your project's root
2. Search and replace in all files
    - search for `custom_extension_key` and `custom-extension-key` to replace them with your **extension key**
3. Adjust the `composer.json` regarding the package name, vendor and autoload section

## Usage

```
$ ddev start
```

Install TYPO3 environments:

```
$ ddev install all
```

Open the setup page:

```
$ ddev launch
```

## Static Code Analysis

```
$ ddev composer check
$ ddev composer fix
```

## Multi-TYPO3

With these features its possible to develop and test your extension with different TYPO3 versions on the same time.

### Background

By running the `ddev install` command, the desired TYPO3 instances will be installed and configured automatically into the `.Build/` directory.

There are two extension installed by default: 

- your **main extension**
- a demo **sitepackage extension**

The main extension is symlinked from the root directory to the `.Build/` directory. This way you can develop your extension in the root directory and test it with different TYPO3 versions.

> [!NOTE]
> This has the small disadvantage, that new files in the root level of your main extension will not be symlinked to the `.Build/` directory. You have to run the `ddev install` command again to update the symlink.

The demo sitepackage extension is a simple extension to test the features of your main extension. You can adjust it to your needs in `Test/.typo3-setup/packages/sitepackage/`.

If you need additional data for the automatic installation process, place a TYPO3 export file in the `Test/.typo3-setup/data` directory.

### Development

You can launch the setup page with the following command:

```shell
$ ddev launch
```

Open a desired TYPO3 instance in your browser:

```shell
$ ddev launch 11
$ ddev launch 12
$ ddev launch 13

$ ddev launch 13 /typo3
```

Run commands in the TYPO3 instance:

```shell
$ ddev 11 composer install
$ ddev 12 typo3 cache:flush
```

## ToDo

- [ ] Add files for static code analysis
- [ ] Add ReST documentation preparation
- [ ] More documentation

## Credits

This repository is partly inspired by the following packages and adjusted to my own needs. 

Github Workflows:
- https://github.com/maikschneider/reusable-workflows

DDEV Setup:
- https://github.com/sourcebroker/t3api
- https://github.com/a-r-m-i-n/ddev-for-typo3-extensions