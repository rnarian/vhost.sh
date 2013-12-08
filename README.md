# vhost.sh

Bash script for managing (add/remove) apache vhosts. 

The Script creates a project directory, a vhost config file and updates `/etc/hosts`. 

Directories may be specified at the beginning of the script.

    hosts_file=/etc/hosts
    www_folder=/Library/Webserver/Sites
    conf_folder=/etc/apache2/extra/sites
    server_reboot="apachectl graceful"

In order to make this thing work `httpd-vhosts.conf` needs to look something like this:

    NameVirtualHost *:80
    (...)
    Include /private/etc/apache2/extra/sites/*.conf

So that any config file within `/private/etc/apache2/extra/sites/` will get included.

## Usage

Add vhost:

    $ sudo vhost -c add -v example.dev

Remove vhost:

    $ sudo vhost -c remove -v example.dev

List vhosts:

    $ vhost -l

### Advanced Usage

Add vhost and restart apache:

    $ sudo vhost -a -c add -v example.dev

Remove vhost and force deletion of project directory:

    $ sudo vhost -f -c remove -v example.dev