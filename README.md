# lsws1clk
[!<Build Status>(https://github.com/litespeedtech/lsws1clk/workflows/lsws1clk/badge.svg)](https://github.com/litespeedtech/lsws1clk/actions/)
[<img src="https://img.shields.io/badge/slack-LiteSpeed-blue.svg?logo=slack">](litespeedtech.com/slack) 
[<img src="https://img.shields.io/twitter/follow/litespeedtech.svg?label=Follow&style=social">](https://twitter.com/litespeedtech)

## Description

`lsws1clk` is a **One-Click Script** for installing LiteSpeed Web Server(LSWS).

It can:

- Install LiteSpeed with default settings.
- Install WordPress with LiteSpeed using `-W` or `--wordpress`.
- Fully provision WordPress using `--wordpressplus`, with optional site settings.
- Use MariaDB by default, or MySQL or Percona Server for MySQL through command-line options.
- Import an existing WordPress installation using `--wordpresspath`.

The script includes a 15-day trial license by default. After the trial period, you can apply your own license or enter your serial number using the --license xxxxxxxx command during installation. Licenses start at $0. <Read more>(https://www.litespeedtech.com/products/litespeed-web-server/lsws-pricing).

## Installation

Common usage:

Install LiteSpeed, LSPHP, MariaDB, WordPress, and LiteSpeed Cache:
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
|  `-L` |`--license`|                      Specifies LSWS serial number.|
|      |`--adminuser <USERNAME>`|          Sets the **WebAdmin Console** username instead of using `admin`. |
| `-A` |`--adminpassword <PASSWORD>`|      Sets the **WebAdmin Console** password instead of generating a random password.|
|      |`--adminport <PORTNUMBER>`|        Sets the **WebAdmin Console** port instead of using `7080`.|
| `-E` |`--email <EMAIL>`|                 Sets the administrator email address.|

### PHP Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |`--lsphp <VERSION>`    |           Sets the LSPHP version, such as `84`. Supported versions are `74` ~ `85`.|

### DataBase Options
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |`--mariadbver <VERSION>`  |        Sets the MariaDB version. Supported versions are `10.6`, `10.11`, `11.4`, and `11.8`.|
| `-R` | `--dbrootpassword <PASSWORD>` |   Sets the database root password.|
|      |  `--dbname <DATABASENAME>` |      Sets the WordPress database name.|
|      |  `--dbuser <DBUSERNAME>`   |      Sets the WordPress database username.|
|      |  `--dbpassword <PASSWORD>` |      Sets the WordPress database-user password.|
|      |  `--prefix <PREFIXNAME>`   |      Sets the WordPress database-table prefix.|
|      |   `--pure-mariadb`|               Installs OpenLiteSpeed and MariaDB.|
|      |   `--pure-mysql`|                 Installs LiteSpeed and MySQL.|
|      |   `--pure-percona`|               Installs LiteSpeed and Percona.|
|      |   `--with-mysql`  |               Installs LiteSpeed/App with MySQL.|
|      |   `--with-percona`  |             Installs LiteSpeed/App with Percona.|

### Application Options
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
| `-W` |`--wordpress`|                     Installs WordPress. You will still need to complete the WordPress setup by browser|
|      |  `--wordpressplus <SITEDOMAIN>`|  Installs, set up, and configure WordPress, also LSCache will be enabled|
|      |  `--wordpresspath <WP_PATH>`|     To specify a location for the WordPress installation or use for an existing WordPress.|
|      |  `--wpuser <WP_USER>`   |         Sets the WordPress admin user for WordPress dashboard login.|
|      |   `--wppassword <PASSWORD>`    |  Sets the WordPress admin user password for WordPress dashboard login.|
|      |   `--wplang <WP_LANGUAGE>` |      Sets the WordPress language. Default value is "en_US" for English.|
|      |   `--sitetitle <WP_TITLE>` |      Sets the WordPress site title. Default value is mySite.|

### System Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |  `--listenport <PORT>`  |         Sets the HTTP server listener port, default is 80.|
|      |  `--ssllistenport <PORT>` |       Sets the HTTPS server listener port, default is 443.|
|      | `--sitedomain <SITEDOMAIN>` |     Set domain name mapping on listener level (default: `*`). |
|      |   `--proxy-r`  |                  Sets a proxy with rewrite type.|
|      |   `--proxy-c`  |                  Sets a proxy with config type.|
|      | `--proxy-port <PORT>` |           Configures proxy port (default: `8080`). |

### Security Configuration
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
|      |   `--owasp-enable`  |             Enables mod_security with OWASP rules. If LSWS is installed, then enable the owasp directly|
|      |   `--owasp-disable`  |            Disables mod_security with OWASP rules.|    
|      |   `--fail2ban-enable`  |          Enables fail2ban for webadmin and wordpress login pages.|

### Control
|  Opt |    Options    | Description|
| :---: | ---------  | ---  |
| `-U` |   `--uninstall`  |                Uninstalls LiteSpeed and remove installation directory.|
| `-P` |   `--purgeall`   |                Uninstalls LiteSpeed, remove installation directory, and purge all data in MySQL.|
| `-Q` |   `--quiet`      |                Uses quiet mode, won't prompt to input anything.|
| `-V` |   `--version`    |                Displays the script version information.|
| `-v` |   `--verbose`    |                Displays more messages during the installation.|
|      |   `--update`      |               Updates lsws1clk from github.|
| `-H` |    `--help`       |               Displays help messages.|



## Usage Examples

### Web Server with PHP

```bash
# Installs LiteSpeed with default PHP Version.
./lsws1clk.sh
```

### WordPress with PHP
```bash
# Installs LiteSpeed with WordPress and MariaDB"
./lsws1clk.sh -W
```

### WordPress with Mysql
```bash
# Installs LiteSpeed with WordPress and Mysql"
./lsws1clk.sh -W --with-mysql
```

### OWASP
```bash
# To enable OWASP feature for LSWS. This single option can be used even if the web server is already installed. 
./lsws1clk.sh --owasp-enable
```

### Proxy custom port
```bash
./ols1clk.sh --proxy-r --proxy-port 7860
```

## FAQ

### How do I create additional Virtual Hosts from the console?

Run the following command to create an additional virtual host. The example document root is `/var/www/www.example.com`. Replace `www.example.com` with your domain.

```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com
```

### How do I create additional Virtual Hosts with WordPress from the console?

The first time you create an additional virtual host, the script requires the database root password from `/usr/local/ols/password`. If you use a custom value, update that file or write the password to `/root/.db_password`:

```
echo 'root_mysql_pass="DB_ROOT_PASSWORD"' > /root/.db_password
```

Then run the following command to create an additional virtual host with the WordPress.
```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com -w
```

### How to I create additional Virtual Hosts and LE certificates from the console?

The first time you create an additional virtual host, the script requires the database root password from `/usr/local/ols/password`. If you use a custom value, update that file or write the password to `/root/.db_password`:

```
/bin/bash <( curl -sk https://raw.githubusercontent.com/litespeedtech/ls-cloud-image/master/Setup/vhsetup.sh ) -d www.example.com -le admin@example.com -f
```
Note: The `-f` option is to force https redirection 

## Support & Feedback
If you still have a question after reading these instructions, you have a few options:
* Join <the GoLiteSpeed Slack community>(https://litespeedtech.com/slack) for real-time discussion
* Report any issue on the <Github lsws1clk>(https://github.com/litespeedtech/lsws1clk/issues) project
* Join the discussion on any LiteSpeed topic on the <LSWS Forum>(https://litespeedtech.com/support/forum/).