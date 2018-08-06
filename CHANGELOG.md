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
