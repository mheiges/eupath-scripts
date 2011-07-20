
Useful scripts for managing WDK-based websites. These currently include hard-coded
paths so strict requirements for directory structure and naming apply.

This is a temporary repository. In the future these scripts will be bundled into an RPM.


## cattail
Place a tail on standard log files used by a WDK-based website that has been
installed using EuPathDB file naming and location conventions.

Run `cattail` without options for help.

Requirements

- Apache logs in /var/log/httpd/<hostname>
- Tomcat logs in /usr/local/tomcat_instances/<instance_name>/logs/<webapp_name>
- Jason Fesler's `xtail` in /usr/local/bin

## xtail
Perl script by Jason Fesler

## rebuilder
Rebuilds an existing WDK-based website owned by the invoking user.

Run `rebuilder` without options for help.

Requirements

- java in one of the locations listed in the `jpath` search path hard-coded in the script.
- `$ORACLE_HOME` in one of the locations listed in the `oracle_paths` hard-coded in the script.
- sudoers permissions to grant users permissions to manage `httpd`. See below.


## ibuilder
Rebuild an existing WDK-based integration website owned by joeuser.

Run `ibuilder` without options for help.

Requirements

- `joeuser` account. This does not need to be a login account (can use `/bin/false` for the shell) unless you plan to also use it for Jenkins jobs.
- The site files must be owned by `joeuser`
- `ibuilder` is a wrapper on `rebuilder` so all the rebuilder requirements also apply.
- sudoers permissions to grant users permissions to run `ibuilder` as `joeuser`. See below.


## example /etc/sudoers
        User_Alias APIDB_DEV_GROUP = joeuser, %www, %cbil
        
        Cmnd_Alias HTTPD_TOMCAT = /usr/local/bin/instance_manager, /etc/init.d/httpd
        
        APIDB_DEV_GROUP ALL = (joeuser) NOPASSWD:/usr/local/bin/ibuilder, NOPASSWD:HTTPD_TOMCAT
