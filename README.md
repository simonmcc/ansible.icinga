ansible.icinga
=========

A simple role for configuring an Icinga server using both ansible inventory data & an external datasource in the form of groupvars.

Requirements
------------

`templates/external_groups.cfg.j2` uses the jinja2 do extension to append items to an array, so you'll need to make sure you're loading the extension, with something like this in your [ansible.cfg](http://docs.ansible.com/ansible/intro_configuration.html#jinja2-extensions):

    jinja2_extensions = jinja2.ext.do
 
Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


	
	adminusers: "icingaadmin,simonm"
	users:
	  icingaadmin:
	    password: icinga
	  simonm:
	    password: icingapass
	
	external_hosts:
	  - fqdn: familytracker.greatershankill.org
	    ipv4: 192.168.28.9
	    services:
	      - name: ssh
	      - name: http_url
	        args: "!familytracker.greatershankill.org!http://familytracker.greatershankill.org/phpinfo.php"


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

	- hosts: all
	  become: yes
	
	  roles:
	    - icinga
         

License
-------

BSD

Author Information
------------------

Simon McCartney, simon@mccartney.ie, please raise issues etc using the [github project](https://github.com/simonmcc/ansible.icinga).