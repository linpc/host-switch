host-switch
====
A CLI tool to easily switch between different hosts settings

Usage
----
1. Prepare your `/etc/hosts` file as the following formats:

        # # begin DEV-my host setting
        # # put any comment / description here if you want
        # 10.1.0.35 my.example.com
        # 10.1.0.36 my2.example.com
        # # end DEV-my host setting

        # # begin STAGING host setting
        # 10.3.0.47 my.example.com
        # 10.3.0.48 my2.example.com
        # # end STAGING host setting

    __Note:__ host setting name (_case-sesitive_, which are `DEV-my` and `STAGING` in the above case) should match on **begin** and **end** line.

2. Then you can use CLI to manage your hosts table switching:

    Show current setting

        $ host-switch

    Turn on `DEV-my` host setting

        $ sudo host-switch on DEV-my

    Turn on `STAGING` host setting (and implicitly turn off other exists setting)

        $ sudo host-switch on STAGING

    Turn off all host setting (will use global DNS lookup)

        $ sudo host-switch all-off

License
----
FreeBSD License
