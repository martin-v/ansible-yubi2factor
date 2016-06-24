Role Name
=========

Configure PAM to enable two-factor authentication with yubikey. Optional is
display locking when the yubikey is remove.

**Attention: Please read and understand the documentation of
the yubi2factor_enforce variable below. This role can lock you completely out of
your system.**


Requirements
------------

The role installs on host:

    * pam_yubico
    * yubikey-personalization-gui

This role is designed to work with a YubiKey from [Yubico, Inc.](http://yubico.com/).


The YubiKey must be configured with following configurations:
* One slot must be configured in SHA/HMAC challenge-response mode
* The serial number must be readable
* challenge-response must be usable without button push


Role Variables
--------------

### Required Variables:

Per default the role only enable single login with YubiKey **or** password. After
you checked the correct functionality of both logins, once with password and
once with YubiKey, you can enable the two-factor condition.

If the the YubiKey login don't work you will have no option to login in your
system after enabling the two-factor condition.

  yubi2factor_enforce: false


### Optional Variables:

This role comes with a automatic screen-saver lock of gnome shell user sessions
when the YubiKey is removed from the machine. To disable this behavior set the
following variable to false.

  yubi2factor_lock_screen_on_remove: true


Dependencies
------------

None.


Example Playbook
----------------

    - hosts: all
      remote_user: root
      vars_files:
        - yubi2factor.yml
      roles:
        - martin-v.yubi2factor


Example variables file
----------------------

TODO


Tips
----

TODO


Open tasks
----------

0. Complete the documentation
  0. Document ~/yubikey_dont_lock_on_next_remove
0. Write <del>more</del> tests
0. Add CI for the role
0. Implement better solution for multiple user


License
-------

MIT

Author Information
------------------

This role was created in 2016 by [Martin V](https://github.com/martin-v).
