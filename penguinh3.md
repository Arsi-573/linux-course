# h3 Hello Web Server

First assingment was to read twon articles about name based Virtual Hosts and summarize both articles. 
#### 1) Name based virtual host
   https://httpd.apache.org/docs/2.4/vhosts/name-based.html

- Apache can host multiple websites on one IP address using name-based virtual hosts.
- Apache selects the correct virtual host by matching the requested hostname against ServerName and ServerAlias directives.
- Virtual hosts are defined using <VirtualHost> blocks, typically differentiated by name rather than IP.
- If no matching virtual host is found, Apache uses the first defined virtual host as the default.
- Each virtual host usually specifies at least ServerName and DocumentRoot.

#### 2) Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address
   https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

- Apache can host multiple websites on one IP address using name-based virtual hosts.
- Each website has its own configuration file in the sites-available directory.
- Virtual host configurations define ServerName, optional ServerAlias, and DocumentRoot.
- Sites are enabled with the a2ensite command and applied by restarting Apache.
- The /etc/hosts file can be used for local testing without real DNS entries.

As we can see, there's a lot in common between these two articles.
