# SHORYUKEN #

Aimed at easy and fast hacking, shoryuken is a linux bash tool designed to get full control of poorly configurated web applications with backend DBMS in the same machine. In its current version, it uses SQL injection techniques to own MYSQL and MSSQL hosts when they run as OS user ROOT with application user having file privileges (Linux MySQL) or as DB sysadmin user with DB running as OS user SYSTEM (Windows MSSQL). It is done using the same unique HTTP request, the shoryuken (that means "rising dragon punch" in japanese).

Takeover is pretty straightforward with a single request issued to open a "custom shell" on Windows using xp\_cmdshell output redirected to a file at default web server root (c:\inetpub\wwwroot) and on Linux using a PHP one line web shell with sudo also at default web server root (/var/www).

The custom shell is provided using default HTTP port 80 (it will be always there) without need to run or download anything and/or relying on firewall's policy.

Shoryuken needs curl installed (Debian-like systems: apt-get install curl).

~~Shoryuken only exploits SQL injection, you need to first find this kind of vulnerability on target using another tool or method.~~

**Shoryuken now scans hosts, searching for top SQL injection entry points (according to @VulnSites) therefore increasing its mass detection rate to punch vulnerability.**

OBS: while there are few systems in these conditions (most likely on internal networks), the vulnerable ones can be easily hacked with shoryuken.

### Demo Video: ###

<a href='http://www.youtube.com/watch?feature=player_embedded&v=5XnpMSvvvso' target='_blank'><img src='http://img.youtube.com/vi/5XnpMSvvvso/0.jpg' width='425' height=344 /></a>

### Usage: ###

> ./shoryuken1.5 [[OPTION](OPTION.md)] {TARGET | INPUT\_FILE} {OUTPUT\_FILE}

> => Rearrange target URL if needed to put **vulnerable parameter** always **at the end**.


### Options: ###

> -h   _help_

> -i   _interactive mode_

> -p   _direct punch_

> -t   _test mode_

> -s   _scan from list_

> -l   _test from list_


### Examples: ###

> ./shoryuken1.5 -i

> ./shoryuken1.5 -p "192.168.0.2/test.asp?id=1"

> ./shoryuken1.5 -p "vuln-site.net/home/news.php?info=text&vuln\_param=11230"

> ./shoryuken1.5 -t "www.example.com/page.php?name=john"

> ./shoryuken1.5 -s hosts.txt mytargets.txt

> ./shoryuken1.5 -l mytargets.txt vulnerables.txt


### Advantages: ###

> - Gets root/system almost instantly;

> - Scans and tests multiple targets;

> - Very simple to use;

> - Very small (just 9k) e portable;

> - Can be easily used in tiny linux systems like mobile ones;

> - Pwns MySQL and MSSQL systems at once;

> - No need to download/upload anything to target;

> - No need for an extra open port on machine or firewall;

> - No need for password(s) stored into database;

> - No need for privilege escalation;

> - Can be easily used when pivoting over linux machines;

> - Minimum footprinting in Test Mode (1 request);

> - Uses filter bypass techniques like hex converting and HPP;

> - Uses statistics from @VulnSites project to improve detection rate;

> - Auto cleaning (except for logs);

> - Fast Hollywood-style hacking, perfect for a live demonstration.

<br>

<b>IMPORTANT: do not use this tool on servers where you don't have permission to do that.</b>


<img src='http://images2.wikia.nocookie.net/__cb20091125000754/streetfighter/images/2/23/Ken-shoryu-ts.gif' />


