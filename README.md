# Flexlm

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Known Issues](#known-issues)
6. [Development](#development)
7. [License](#license)
8. [Author Information](#author-information)

## Overview

A role to manage Flexlm daemon.

## Role Variables

* **flexlm__packages_state** : State of package(s) [default : `present`].
* **flexlm__packages_manage** : If package(s) should be managed with this role [default : `True`].
* **flexlm__dependent_packages** : List of additional packages requested as 'flexlm' dependencies [default : `lsb-core`, `unzip`]
* **flexlm__lmgrd_version** : Version of `lmgrd` to use [default : `11.14.0.1`].
* **flexlm__lmgrd_source** : Source of the `lmgrd` bin to send [default : `usr/local/bin/lmgrd`].
* **flexlm__lmgrd_path** : The place to store `lmgrd` bin [default : `/usr/local/bin/lmgrd`].
* **flexlm__lmutil_source** : Source of the `lmutil` bin to send [default : `usr/local/bin/lmutil`].
* **flexlm__lmutil_path** : The place to store `lmutil` bin [default : `/usr/local/bin/lmutil`].
* **flexlm__user_name** : Username used to launch `lmgrd` [default : `flexlm`].
* **flexlm__licence_file** : Licence file to deserve [default : `/opt/flexlm/VENDOR/licence.lic`].
* **flexlm__licences** : Lists to manage vendor daemon and licence files [default : `[]`].
* **flexlm__service_manage** : If Licence Manager service should be managed with this role [default : `True`].
* **flexlm__service_enabled** : If Licence Manager service should be enable at startup [default : `True`].
* **flexlm__service_unit_content** : Template used to generate the previous file [default : `etc/systemd/system/flexlm.service.j2`].

## Example Playbook

* Manage Flexlm with defaults vars :

``` yaml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.flexlm
```

* Manage Flexlm to provide Intel Fortran (without binaries) :

``` yaml
- hosts: intel-lm
  roles:
    - role: ipr-cnrs.flexlm
      flexlm__licences:
        - name: intel
          description: 'flexlm Licence Manager for Matlab'
          bin_path: '/opt/intel/bin'
          lic_path: '/opt/matlab/etc/licence.lic'          # need to be a file
```

* Manage Flexlm to provide Matlab Licence and vendor daemon binaries :

```yaml
- hosts: matlab-lm
  roles:
    - role: ipr-cnrs.flexlm
      flexlm__licences:
        - name: matlab
          description: 'flexlm Licence Manager for Matlab'
          bin_path: '/opt/matlab/bin'
          bin_src: '{{ inventory_dir + "/../resources/service/matlab-lm/bin/" }}'
          lic_path: '/opt/matlab/etc/licence.lic'                                                # need to be a file
          lic_src: '{{ inventory_dir + "/../resources/host/matlab-lm.domain/etc/licence.lic" }}' # need to be a file
```

## Configuration

This role will :
* Copy the `lmgrd` and `lmutil` binaries to the client.
* Create a specific user to launch daemon.
* Set up a systemd service (flexlm-NAME). [Thanks to Kalebo instructions][kalebo instruction flexlm systemd].
* Copy vendor daemon binaries to the host if source is specified.
* Copy licence file to the host if source is specified.

The `lmgrd` and `lmutil` binaries comes from [Mathworks][mathworks download url] in version **flexlm__lmgrd_version**.

## Known Issues

* If a value of one licence change in **flexlm__licences** var, all services will be restarted.

## Development

This source code comes from our [Gogs instance][flexlm source] and the [Github repo][flexlm github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR anywhere :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][flexlm source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][flexlm source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[gogs to github hook]: https://stackoverflow.com/a/21998477
[flexlm source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.flexlm
[flexlm github]: https://github.com/ipr-cnrs/flexlm
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/
[mathworks download url]: https://fr.mathworks.com/support/install/license_manager_files.html
[kalebo instruction flexlm systemd]: https://gist.github.com/kalebo/fd39edb6c6e4ebed41f7eab2d9925ebc
