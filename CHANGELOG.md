
## v1.x

### Features
* Add a way to provide vendor daemon binaries and licence file.
* Manage services for the lists var (flexlm__licences).
* Allow to manage several licences on a same host (close #1).

### Enhancements
* Set a var to manage the state of the deployment by this role.

## v1.0

### Features
* Install FlexLM dependencies.
* Copy `lmgrd` and `lmutil` binaries.
* Ensure to have a symlink for `lmgrd` to it's last version.
* Create a specific user to launch `lmgrd`.
* Set up a systemd service.
* Possibility to set working directory and licence file in the service unit.
