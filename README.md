xbps-repoconf
====


What is does this role do?
--------------------------

This role configures the XBPS repositories used by the system.  It is
commonly used to ensure that all systems at a particular site are
using the same mirror, and to enable local builders on managed
systems.

Meta
----

Files Managed:
  * /etc/xbps.d/00-repository-main.conf
  * /etc/xbps.d/10-repository-nonfree.conf
  * /etc/xbps.d/10-repository-multilib.conf
  * /etc/xbps.d/10-repository-multilib-nonfree.conf
  * [Custom Repositories]

Defaults Provided:
  * xbps_repository_main: https://repo.voidlinux.eu/current
  * xbps_repository_nonfree: https://repo.voidlinux.eu/current/nonfree
  * xbps_repository_multilib: https://repo.voidlinux.eu/current/multilib
  * xbps_repository_multilibe_nonfree: https://repo.voidlinux.eu/current/multilib/nonfree
  * xbps_repository_address: repo.voidlinux.eu
  * xbps_repository_port: 443

Variables Required:
  * None

Optional Variables:
  * xbps_repoconf_repos: A dictionary of dictionaries in the format shown below:

```
[repo name]:
  - address: Full address with protocol for the repo
  - serveraddr: Address in dotted form for the repo
  - serverport: Port number the repo listens on
  - fingerprint: The repo's signing key fingerprint
```

Files Required:
  * None

Optional Files:
  * assets/xbps/<fingerprint>.plist - A plist file must exist for every custom repo that is to be configured.  This file is in the same format as /var/db/xbps/keys*.plst  The assets tree may exist anywhere that ansible can find it, but it is suggested to put it in the working directory which contains roles/, host_vars/, etc. since multiple roles expect files to be available in this tree.

Conflicting Roles:
  * None

Depends On:
  * [network](https://github.com/void-ansible-roles/network)
