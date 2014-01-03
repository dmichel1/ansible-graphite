Ansible - Metrics
-----------------

Tested with Ansible 1.4.1 against RHEL/CentOS 6.4. 


This Ansible playbook will install graphite via pip in its default location '/opt/graphite'


To run this playbook.

1. clone the repo
2. modify `hosts` file with the IP or hostname of the server you want to setup
3. ignore ssh's known hosts file
  * `export ANSIBLE_HOST_KEY_CHECKING=False`
4. run `ansible-playbook -i hosts playbook.yml`
5. In ~4 minutes you should have a running Graphite/Statd server!
  * I've been testing this on a Digital Ocean VM - 1 CPU/1GB Ram CentOS 6.4


Graphite
--------
Graphite will be installed via pip in its default location '/opt/graphite'


Statsd
------
Ansible will setup statsd to communicate with a Graphite server running on localhost by default.


Carbon's Storage Schema and Aggregation configuration have been setup according to [this page](https://github.com/etsy/statsd/blob/master/docs/graphite.md).




TODO
----
* Automate Django superuser creation `python manage.py createsuperuser`.
* Add Debian support




Resources
---------
* http://graphite.wikidot.com/quickstart-guide
