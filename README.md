# lsws1clk
[![Build Status](https://github.com/litespeedtech/lsws1clk/workflows/lsws1clk/badge.svg)](https://github.com/litespeedtech/lsws1clk/actions/)
[<img src="https://img.shields.io/badge/slack-LiteSpeed-blue.svg?logo=slack">](litespeedtech.com/slack) 
[<img src="https://img.shields.io/twitter/follow/litespeedtech.svg?label=Follow&style=social">](https://twitter.com/litespeedtech)
## Description

lsws1clk is a one-click installation script for LiteSpeed. Using this script, you can quickly and easily install LiteSpeed with it’s default settings. We also provide a **-W** parameter that will install WordPress at the same time but it must still be configured through the wp-config.php page. By default, a MariaDB database will be set up using this script, you can also specify other DB if needed. If you already have a WordPress installation running on another server, it can be imported into LiteSpeed with no hassle using the **--wordpresspath** parameter. To completely install WordPress with your LiteSpeed installation, skipping the need for the wp-config.php page, use the **--wordpressplus** flag. This can be used with **--wpuser**, **--wppassword**, **--wplang**, and **--sitetitle** to configure each of the settings normally set by wp-config.php.

The script includes a 15-day trial license by default. After the trial period, you can apply your own license or enter your serial number using the --license xxxxxxxx command during installation. Licenses start at $0. [Read more](https://www.litespeedtech.com/products/litespeed-web-server/lsws-pricing).

## Installation

Our One-Click script comes with several options. Here are two commmon usages.

Install LiteSpeed, LSPHP, MariaDB, WordPress, and LiteSpeed Cache plugin:
```
bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/lsws1clk/master/lsws1clk.sh ) -w
```

Install LiteSpeed and LSPHP only:
```
bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/lsws1clk/master/lsws1clk.sh )
```

See below for additional options and usage examples.

### Options:
### Essential Options
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|  `-L` |`--license`|                       To use specified LSWS serial number.|
|      |`--adminuser [USERNAME]`|          To set the WebAdmin username for LiteSpeed instead of admin.|
| `-A` |`--adminpassword [PASSWORD]`|      To set the WebAdmin password for LiteSpeed instead of using a random one.|
|      |`--adminport [PORTNUMBER]`|          To set the WebAdmin console port number instead of 7080.|
| `-E` |`--email [EMAIL]`|                 To set the administrator email.|

### PHP Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |`--lsphp [VERSION]`    |           To set the LSPHP version, such as 83. We currently support versions '74, 81~84'.|

### DataBase Options
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |`--mariadbver [VERSION]`  |        To set MariaDB version. We currently support versions up to 11.8.|
| `-R` | `--dbrootpassword [PASSWORD]` |   To set the database root password.|
|      |  `--dbname [DATABASENAME]` |      To set the database name to be used by WordPress.|
|      |  `--dbuser [DBUSERNAME]`   |      To set the WordPress username in the database.|
|      |  `--dbpassword [PASSWORD]` |      To set the WordPress table password in MySQL.|
|      |  `--prefix [PREFIXNAME]`   |      To set the WordPress table prefix.|
|      |   `--pure-mariadb`|               To install LiteSpeed and MariaDB.|
|      |   `--pure-mysql`|                 To install LiteSpeed and MySQL.|
|      |   `--pure-percona`|               To install LiteSpeed and Percona.|
|      |   `--with-mysql`  |               To install LiteSpeed/App with MySQL.|
|      |   `--with-percona`  |             To install LiteSpeed/App with Percona.|

### Application Options
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
| `-W` |`--wordpress`|                     To install WordPress. You will still need to complete the WordPress setup by browser|
|      |  `--wordpressplus [SITEDOMAIN]`|  To install, set up, and configure WordPress, also LSCache will be enabled|
|      |  `--wordpresspath [WP_PATH]`|     To specify a location for the WordPress installation or use for an existing WordPress.|
|      |  `--wpuser [WP_USER]`   |         To set the WordPress admin user for WordPress dashboard login.|
|      |   `--wppassword [PASSWORD]`    |  To set the WordPress admin user password for WordPress dashboard login.|
|      |   `--wplang [WP_LANGUAGE]` |      To set the WordPress language. Default value is "en_US" for English.|
|      |   `--sitetitle [WP_TITLE]` |      To set the WordPress site title. Default value is mySite.|

### System Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |  `--listenport [PORT]`  |         To set the HTTP server listener port, default is 80.|
|      |  `--ssllistenport [PORT]` |       To set the HTTPS server listener port, default is 443.|
|      |   `--proxy-r`  |                  To set a proxy with rewrite type.|
|      |   `--proxy-c`  |                  To set a proxy with config type.|

### Security Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |   `--owasp-enable`  |             To enable mod_security with OWASP rules. If LSWS is installed, then enable the owasp directly|
|      |   `--owasp-disable`  |            To disable mod_security with OWASP rules.|    
|      |   `--fail2ban-enable`  |         To enable fail2ban for webadmin and wordpress login pages.|

### Control
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
| `-U` |   `--uninstall`  |                To uninstall LiteSpeed and remove installation directory.|
| `-P` |   `--purgeall`   |                To uninstall LiteSpeed, remove installation directory, and purge all data in MySQL.|
| `-Q` |   `--quiet`      |                To use quiet mode, won't prompt to input anything.|
| `-V` |   `--version`    |                To display the script version information.|
| `-v` |   `--verbose`    |                To display more messages during the installation.|
|      |   `--update`      |               To update lsws1clk from github.|
| `-H` |    `--help`       |               To display help messages.|



## Usage Examples

### Web Server with PHP

```bash
# To install LiteSpeed with default PHP Version.
./lsws1clk.sh
```

### WordPress with PHP
```bash
# To install LiteSpeed with WordPress and MariaDB"
./lsws1clk.sh -W
```

### WordPress with Mysql
```bash
# To install LiteSpeed with WordPress and Mysql"
./lsws1clk.sh -W --with-mysql
```

### OWASP
```bash
# To enable OWASP feature for LSWS. This single option can be used even if the web server is already installed. 
./lsws1clk.sh --owasp-enable
```

## FAQ

### How do I create additional Virtual Hosts from the console?
Run the following command to create an additional virtual host in a few seconds. The example document root will be **/var/www/www.example.com**. Be sure to substitute your own domain. 
```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com
```

### How do I create additional Virtual Hosts with WordPress from the console?
The first time you create an additional Virtual Host, the script will need to get your database root password from **/usr/local/lsws/password**. If you have custom value, please update **/usr/local/lsws/password** or echo the password to the specified location: **/root/.db_password**. 
```
echo 'root_mysql_pass="DB_ROOT_PASSWORD"' > /root/.db_password
```

Then run the following command to create an additional virtual host with the WordPress.
```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com -w
```

### How to I create additional Virtual Hosts and LE certificates from the console?
Please be sure that your domain is already pointing to the server.

Then run the following command to create an additional virtual host with a Let's Encrypt certificate applied. Be sure to substitute your own domain and your email address. 
```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com -le admin@example.com -f
```
Note: The `-f` option is to force https redirection 

## Support & Feedback
If you still have a question after reading these instructions, you have a few options:
* Join [the GoLiteSpeed Slack community](https://litespeedtech.com/slack) for real-time discussion
* Report any issue on the [Github lsws1clk](https://github.com/litespeedtech/lsws1clk/issues) project
* Join the discussion on any LiteSpeed topic on the [LSWS Forum](https://litespeedtech.com/support/forum/).