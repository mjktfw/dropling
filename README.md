# Dropling

## Purpose

Use as a submodule to deploy Linux projects.

## Assumptions

- `make`, `install`, `uninstall`  are the only required subcomannds to execute `drop` submodule functions
- `make` is independent of system file hierarchy and prepares the file structure of the `app` directory
- `install` and `uninstall` may require editing non-standard locations in `app.conf` depending on system
- usage might require editing of `user.conf` files

## Structure

- submodule directory: `./drop/`
- per-project dependecnies: `./deps.d/`

## Usage

### Get repository

- `clone` remote project repository to local machine: `git clone https://github.com/user/repo`
- `init` submodules, especially to get this one: `./init`

### Prepare repository locally

- `make` repo: `./run make`:
  - detach from git (.gitignore)
  - setup internal file structure
  - setup default config files

### Install repository to OS

- (optional) modify paths in `app.conf` to change default installation paths
- `install` installs the repository to OS
  - `uninstall` current version
  - install `dependencies`: `~/.profile.d/*.sh` sourced to set env vars on shell launch
  - setup `profiledir` to easily access environment variables
  - `link` binaries, configs and data to follow 'XDG Base Directory Specification'
- (optional) `hook` git's post-merge hook for automatic upgrades on git pull: `./run hook up`

### Aliases

- `quick`: `./run quick` for `install` + `hook up`
