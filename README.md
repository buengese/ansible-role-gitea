ansible-role-gitea
==================
This role installs and manages [gitea](https://gitea.io). A painless self-hosted Git service.
Gitea is a community managed lightweight code hosting solution written in Go.

Sample Usage
------------
```yaml
- name: "Install gitea"
  hosts: git.example.com
  roles:
    - buengese.gitea
  vars:
    # Here we assume we are behind a reverse proxy that will
    # handle https for us, so we bind on localhost:3000 using HTTP
    gitea_fqdn: 'git.example.com'
    gitea_root_url: 'https://git.example.com'
    gitea_protocol: http

    gitea_start_ssh: true
```


Role Variables
--------------

The following variables determine the install and update behaviour of this role.

* `gitea_version`: Define an exact version of gitea to install or use 'latest' to install the latest version. (Default `1.18.3`)
* `gitea_version_check`: Check if install version != `gitea_version` before starting the download. (Default `true`)
* `gitea_gpg_key`: The gpg key with which the binary is signed.
* `gitea_gpg_server`: A gpg key server where this role can download the gpg key

The following variables should always be changed.

* `gitea_fqdn`: The full domain name for the gitea server.
* `gitea_root_url`: The http/https root url.

### Optional Variables

This role also defines variables for most of the gitea configuration see [defaults/main.yml](defaults/main.yml) for a full list. The function of these variables is explained in the gitea [config cheat-sheet](https://docs.gitea.io/en-us/config-cheat-sheet/).


Supported OS
------------
- Ubuntu 20.04
- Debian 10
- Debian 11
- Fedora 35
- ArchLinux


License
-------

BSD-3-Clause
