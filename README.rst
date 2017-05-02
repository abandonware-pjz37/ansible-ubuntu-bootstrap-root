Ubuntu Bootstrap Root
=====================

.. image:: https://travis-ci.org/ansible-stuff/ubuntu-bootstrap-root.svg?branch=master
  :target: https://travis-ci.org/ansible-stuff/ubuntu-bootstrap-root/builds

Ansible role for initializing Ubuntu remote (root part):

* Increase security of SSH service by `ansible-stuff.ssh <https://galaxy.ansible.com/ansible-stuff/ssh/>`__
* Setup autoupgrade by `jnv.unattended-upgrades <https://galaxy.ansible.com/jnv/unattended-upgrades/>`__
* Create new sudo user with ``zsh`` shell
* Add ``id_rsa.pub`` from local machine to ``.ssh/authorized_keys`` on remote

**!!! WARNING:** This script will **disable** SSH password authentication **!!!**

Usage
-----

Clone playbook:

.. code-block:: none

  > git clone https://github.com/ansible-stuff/ubuntu-bootstrap-root
  > cd ubuntu-bootstrap-root
  [ubuntu-bootstrap-root]>

Create inventory file ``hosts``:

.. code-block:: ini

  [ubuntu-bootstrap-root]
  mymachine

Use sample file to create host variables:

.. code-block:: none

  [ubuntu-bootstrap-root]> mkdir host_vars/
  [ubuntu-bootstrap-root]> cp sample/mymachine.yml host_vars/

Update content of this file:

.. code-block:: none

  [ubuntu-bootstrap-root]> vim host_vars/mymachine.yml

Role Variables
--------------

============================== ==============================
Name                           Description
============================== ==============================
ubuntu_bootstrap_user_name     Name of newly created user
ubuntu_bootstrap_user_password Password of newly created user
============================== ==============================

Password can be created by command ``mkpasswd --method=sha-512``
(on Ubuntu it can be installed by ``apt-get install -y whois``).

Run Playbook
------------

Install dependencies:

.. code-block:: none

  [ubuntu-bootstrap-root]> ansible-galaxy install -r requirements.txt -p _3rdParty/roles

Run playbook:

.. code-block:: none

  [ubuntu-bootstrap-root]> ansible-playbook --inventory-file hosts role.yml

License
-------

`BSD <https://github.com/ansible-stuff/ubuntu-bootstrap-root/blob/master/LICENSE>`__

Author Information
------------------

Ruslan Baratov <ruslan_baratov@yahoo.com>
