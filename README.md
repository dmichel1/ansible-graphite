[![Build Status](https://travis-ci.org/dmichel1/ansible-graphite.png?branch=master)](https://travis-ci.org/dmichel1/ansible-graphite)

Ansible - Graphite: Scalable Realtime Graphing
------------------
This Ansible playbook will install graphite via pip in its default location '/opt/graphite'


To run this playbook.

1. clone the repo
2. modify the `hosts` file to reflect the server you want to install Graphite on
3. ignore ssh's known hosts file
  * `export ANSIBLE_HOST_KEY_CHECKING=False`
4. run `ansible-playbook -i hosts playbook.yml`
  * You can modify the user Ansible uses by adding extra-vars `ansible-playbook -i hosts playbook.yml --extra-vars ssh_user=ec2-user`
5. In ~4 minutes you should have a running Graphite server!



What you need to change
-----------------------
## Secrets
Change `graphite_secret_key` under `roles/graphite/defaults/main.yml` to something unique for your graphite instance!

## Django
Change `graphite_django_admin_media` under `roles/graphite/defaults/main.yml` to the path of your django admin media
```
    # XXX In order for the django admin site media to work you
    # must change @DJANGO_ROOT@ to be the path to your django
    # installation, which is probably something like:

    Alias /media/ "/usr/local/lib/python2.7/dist-packages/django/contrib/admin/static/admin/"
    # or 
    #Alias /media/ "/usr/lib/python2.6/site-packages/django/contrib/admin/media/"
```

## Carbon Storage and Aggregation
It has been setup according to [this page](https://github.com/etsy/statsd/blob/master/docs/graphite.md) and might not do what you expect to with your data


Testing
--------

### Vagrant
Simply clone this repo and make sure you have Vagrant + Virtual Box installed and...
  1. vagrant up
  2. visit http://192.168.111.222/
  3. :-) 

Vagrant is using Ubuntu 14.04 Trusty Tahr for it's OS.


### Digital Ocean
I've tested this playbook with Digital Ocean VM's with a few different flavor of OS's.

  * CentOS 6.5
  * Ubuntu 14.04 Trusty Tahr

### AWS EC2
  * Amazon Linux



TODO
----
* Add Django superuser creation `python manage.py createsuperuser`.


Known Issues
------------
* If you are seeing "DatabaseError: database is locked" in your graphite logs, restarting apache may fix the issue for you. 
* SELinux needs to be disabled


Resources
---------
* http://graphite.wikidot.com/quickstart-guide
