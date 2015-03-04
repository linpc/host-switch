host-switch
====
A CLI tool to easily switch between different hosts settings

Commands
----
    $ host-switch help
    Usage:
        host-switch                     show current setting
        host-switch list <set>          show current setting of specific set
        host-switch dig <set>           show current host table of specific set
        host-switch all-off <set>       (root) turn off all local settings (Use DNS)
        host-switch on <set> <group>    (root) to switch <group> hosts setting ON

Definition
----
* __GROUP__: indicate one specific setting of some hostnames
* __SET__: indicate an aggregation of hosts. You can define several setting __*group*__ for one __*set*__, but only one __*group*__ setting can be activated simultaneously.


Usage
----
0. For example, I have two host-set in my daily development, say _foo_ and _bar_.

1. So I prepare my `/etc/hosts` file as the following formats:

        # # begin foo:DEV-my host setting
        # # put any comment / description here if you want
        # 10.1.0.35 my.foo.com
        # 10.1.0.36 my2.foo.com
        # # end foo:DEV-my host setting

        # # begin foo:STAGING host setting
        # 10.3.0.47 my.foo.com
        # 10.3.0.48 my2.foo.com
        # # end foo:STAGING host setting

        # # begin bar:QA host setting
        # 10.2.0.100 my.bar.net
        # 10.2.0.110 my2.bar.net
        # # end bar:QA host setting

        # # begin bar:testing host setting
        # 10.2.10.33 my.bar.net
        # 10.2.10.39 my2.bar.net
        # # end bar:testing host setting

    __Note:__ host setting name (_case-sesitive_, which are `DEV-my` and `STAGING` in the above case) should match on **begin** and **end** line.

2. Then I can use CLI to manage my hosts table switching:

    Show current setting

        $ host-switch

    Show current setting for `foo` set

        $ host-switch list set

    Turn on `DEV-my` host setting for `foo` set

        $ sudo host-switch on foo DEV-my

    Turn on `STAGING` host setting (and implicitly turn off other exists setting)

        $ sudo host-switch on foo STAGING

    Turn off all host setting (will use global DNS lookup)

        $ sudo host-switch all-off foo

    Are you lazy to type password for `sudo`? Then you can use the shell feature. After the shell prompt, all the commands are the same as the CLI mode, but don't need to type the script name (*i.e.*, `host-switch` should be stripped).

        $ sudo host-switch shell

License
----
FreeBSD License
