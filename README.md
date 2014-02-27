[![Build Status](https://travis-ci.org/dmichel1/ansible-graphite.png?branch=dmichel/travis_ci)](https://travis-ci.org/dmichel1/ansible-graphite)

Ansible - Graphite: Scalable Realtime Graphing
------------------
This Ansible playbook will install graphite via pip in its default location '/opt/graphite'


To run this playbook.

1. clone the repo
2. modify the `hosts` file to reflect the server you want to install Graphite on
3. ignore ssh's known hosts file
  * `export ANSIBLE_HOST_KEY_CHECKING=False`
4. run `ansible-playbook -i hosts playbook.yml`
5. In ~4 minutes you should have a running Graphite server!



What you need to change
-----------------------
## Secrets
Change `graphite_secret_key` under `roles/graphite/defaults/main.yml` to something unique for your graphite instance!

## Django
Ensure the path to Django media is correct for your distro
```
    # XXX In order for the django admin site media to work you
    # must change @DJANGO_ROOT@ to be the path to your django
    # installation, which is probably something like:

    Alias /media/ "/usr/lib/python2.6/site-packages/django/contrib/admin/media/"
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

Vagrant is using Ubuntu 13.04 Raring Ringtail for it's OS.


### Digital Ocean
I've tested this playbook with Digital Ocean VM's with a few different flavor of OS's.

  * CentOS 6.5  
  * Ubuntu 12.04 Precise Pangolin
  * Ubuntu 13.04 Raring Ringtail



TODO
----
* Add Django superuser creation `python manage.py createsuperuser`.



Resources
---------
* http://graphite.wikidot.com/quickstart-guide
