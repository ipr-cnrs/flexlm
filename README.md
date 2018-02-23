# Flexlm

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

A role to manage Flexlm daemon.

## Role Variables

* **flexlm__packages_state** : State of package(s) [default : `present`].
* **flexlm__packages_manage** : If package(s) should be managed with this role [default : `True`].
* **flexlm__dependent_packages** : List of additional packages requested as 'flexlm' dependencies [default : `lsb-core`, `unzip`]

## Example Playbook

* Manage Flexlm with defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.flexlm
```

## Configuration

This role will :
* Do nothing right now.

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
