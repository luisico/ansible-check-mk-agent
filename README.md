Check_MK agent
==============
Install [Check_MK Agent](http://mathias-kettner.com/checkmk.html).

Check_MK agent uses xinetd, which is also installed with this role. The xinetd configuration for Check_MK agent can be found in `/etc/xinetd.d/check-mk-agent`. Note that Check_MK agent listens by default on port '6556' but this role does not manage the firewall.

The agent is installed from the EPEL repository or your Check_MK site. EPEL is used if `check_mk_agent_rpm_url` is blank (default). Additional plugins will be installed if listed in `check_mk_agent_plugins` (as full url). Note that switching from the agent source only works when upgrading the rpm package.

Note that EPEL modifies the location of `MK_LIBDIR` from the default `/usr/lib/check_mk_agent` to `/usr/share/check-mk-agent`. This directory can be set in this role in `check_mk_agent_libdir`.

Requirements
------------
See `meta/main.yml`.

Role Variables
--------------
See `defaults/main.yml` for all options.

Dependencies
------------
EPEL repositories need to be available, ie using role `geerlingguy.repo-epel`.

Example Playbook
----------------
Example:
```
- hosts: servers
  roles:
    - check-mk-agent
```

TODO
----
- Install a specific version using EPEL.
- Support upgrades and downgrades from EPEL and a Check_MK site.
- Check if firewall port is open.
- Support local checks in MK_LIBDIR/local.

Licence
-------
Released under the [MIT license](https://opensource.org/licenses/MIT).

Author Information
------------------
Luis Gracia while at [The Rockefeller University](https://www.rockefeller.edu):
- lgracia [at] rockefeller.edu
- GitHub at [luisico](https://github.com/luisico)
- Galaxy at [luisico](https://galaxy.ansible.com/luisico)
