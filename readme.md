Ansible Graphite
----------------

Use Ansible to install and configure graphite for a RHEL 6.X Operating System. 

This Ansible playbook will install graphite via pip in its default location '/opt/graphite'


To run this playbook.

1. clone the repo
2. modify `hosts` with the IP or hostname of the server you want to setup
3. run `ansible-playbook -i hosts playbook.yml` 




TODO
----
* Automate superuser creation `python manage.py createsuperuser`




Resources
---------
* http://graphite.wikidot.com/quickstart-guide
