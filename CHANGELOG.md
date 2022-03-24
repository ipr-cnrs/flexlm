## v2.3.0
### Enhancements
* Upgrade lmgrd and lmutil daemon to version 11.18.1.

## v2.2.0

### Enhancements
* Ensure to install requirements on Debian Stretch.
* Empty requirements packages by default cause `lsb-compat` is no longer available on Debian Buster.
* Ensure lib64 ld-linux symlinks exists.
* Now works with Debian Buster.

## v2.1.4
### Enhancements
* Upgrade lmgrd and lmutil daemon to version 11.16.2.1.

## v2.1.3

### Enhancements
* Use to_nice_json to manage packages list.

## v2.1.2

* Fix E405 Remote package tasks should have a retry.
* Fix E303 systemctl used in place of systemd module.
* Fix E503 Tasks that run when changed should likely be handlers. Daemon_reload moved to handlers file.

## v2.1.1

### Fixes
* Fix some warnings from ansible-lint.
* Set empty dependencies line to fix Galaxy warning.

## v2.1

### Fixes
* Add a missing ")" in the handler.
* Create a symlink (/usr/tmp) to /tmp to avoid error (fix #2).

## v2.0

### Features
* Add a way to provide vendor daemon binaries and licence file.
* Manage services for the lists var (flexlm__licences).
* Allow to manage several licences on a same host (close #1).
* The **RestartSec** argument for the service can be set, cause some vendor daemon have a timewait greater than 60 seconds.

### Enhancements
* Set a var to manage the state of the deployment by this role.
* Ensure to stop and disable services if deploy state is "absent".
* Add more informations about flexlm__licences var.

## v1.0

### Features
* Install FlexLM dependencies.
* Copy `lmgrd` and `lmutil` binaries.
* Ensure to have a symlink for `lmgrd` to it's last version.
* Create a specific user to launch `lmgrd`.
* Set up a systemd service.
* Possibility to set working directory and licence file in the service unit.
