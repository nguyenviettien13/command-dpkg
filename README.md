# Giới thiệu về dpkg
DPKG là chương trình chính quản lí gói trong Debian. Nó sử dụng để install, build, remove, và manage các gói. Aptitude là front-end chính cho dpkg.
Dưới đây một số lệnh dpkg thường được sử dụng.
### 1. Cài đặt gói
Để cài đặt một gói ".deb", sử dụng lệnh với tùy chọn "-i". Ví dụ để cài đặt một gói ".deb" như "mysql-server-wsrep-5.5.28-23.7-amd64.deb" sử dụng lệnh sau đây.
 ```
	dpkg -i mysql-server-wsrep-5.5.28-23.7-amd64.deb
 ```
Kết quả
 ````
	tiennv000@td:~/Downloads$ sudo dpkg -i mysql-server-wsrep-5.5.28-23.7-amd64.deb (Reading database ... 213593 files and directories currently installed.)
	Preparing to unpack mysql-server-wsrep-5.5.28-23.7-amd64.deb ...
	Unpacking mysql-server-wsrep (5.5.28-23.7) over (5.5.28-23.7) ...
	dpkg: dependency problems prevent configuration of mysql-server-wsrep:
	 mysql-server-wsrep depends on libdbi-perl; however:
	  Package libdbi-perl is not installed.
	 mysql-server-wsrep depends on libdbd-mysql-perl (>= 1.2202); however:
	  Package libdbd-mysql-perl is not installed.
	 mysql-server-wsrep depends on libaio1; however:
	  Package libaio1 is not installed.
	 mysql-server-wsrep depends on mysql-client; however:
	  Package mysql-client is not installed.

	dpkg: error processing package mysql-server-wsrep (--install):
	 dependency problems - leaving unconfigured
	Processing triggers for systemd (229-4ubuntu16) ...
	Processing triggers for ureadahead (0.100.0-19) ...
	Processing triggers for man-db (2.7.5-1) ...
	Errors were encountered while processing:
	 mysql-server-wsrep
 ````
### 2. Hiển thị các gói đã cài đặt
Để xem một gói phần mềm cụ thể đã được cài đặt hay chưa sử dụng tùy chọn "-l" và tên gói, ví dụ kiểm tra xem gói "mysql-server-wsrep", Thực hiện lệnh:
 ```
	dpkl -l mysql-server-wsrep
 ```
 ````
	tiennv000@td:~$ dpkg -l yelp
	Desired=Unknown/Install/Remove/Purge/Hold
	| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
	|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
	||/ Name           Version      Architecture Description
	+++-==============-============-============-=================================
	ii  yelp           3.18.1-1ubun amd64        Help browser for GNOME
 ````

### 3. Remove gói
Để Remove gói ".deb" ta phải xác định tên gói là "mysql-server-wsrep" không phải tên gốc "mysql-server-wsrep-5.5.28-23.7-amd64.deb". Sử dụng tùy chọn "-r" để remove/uninstall gói.
 ```
dpkg -r mysql-server-wsrep
 ```
Có thể sử dụng "-p" thay cho "-r" thì nó sẽ loại bỏ các gói cùng với các file cấu hình, với "-r" dpkg sẽ chỉ bỏ các fois mà không xóa phần file cấu hình.
 ````
	dpkg -p mysql-server-wsrep 
 ````

#### 4. Xem nội dung của một gói
  Để xem nội dụng của một gói phần mềm, dùng tùy chọn "-c" để show. Câu lệnh này sẽ hiển thị nội dung của một gói ".deb" theo dạng danh sách.
 ```
    dpkg -c mysql-server-wsrep-5.5.28-23.7-amd64.deb
 ```
 ````
tiennv000@td:~/Downloads$ dpkg -c mysql-server-wsrep-5.5.28-23.7-amd64.deb
drwxr-xr-x root/root         0 2012-11-29 05:17 ./
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/logrotate.d/
-rwxr-xr-x root/root       837 2012-11-29 05:17 ./etc/logrotate.d/mysql-server
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/init.d/
-rwxr-xr-x root/root      6044 2012-11-29 05:17 ./etc/init.d/mysql
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/logcheck/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/logcheck/ignore.d.server/
-rw-r--r-- root/root      2270 2012-11-29 05:17 ./etc/logcheck/ignore.d.server/mysql-server-5_5
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/logcheck/ignore.d.workstation/
-rw-r--r-- root/root      2270 2012-11-29 05:17 ./etc/logcheck/ignore.d.workstation/mysql-server-5_5
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/logcheck/ignore.d.paranoid/
-rw-r--r-- root/root       712 2012-11-29 05:17 ./etc/logcheck/ignore.d.paranoid/mysql-server-5_5
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/mysql/
-rwxr-xr-x root/root      1198 2012-11-29 05:17 ./etc/mysql/debian-start
drwxr-xr-x root/root         0 2012-11-29 05:17 ./etc/mysql/conf.d/
-rw-r----- mysql/mysql    3610 2012-11-29 05:17 ./etc/mysql/conf.d/wsrep.cnf
-rw-r--r-- root/root        21 2012-11-29 05:17 ./etc/mysql/conf.d/mysqld_safe_syslog.cnf
drwxr-xr-x mysql/root        0 2012-11-29 05:17 ./var/
drwxr-xr-x mysql/root        0 2012-11-29 05:17 ./var/run/
drwxr-xr-x mysql/root        0 2012-11-29 05:17 ./var/run/mysqld/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/sbin/
-rwxr-xr-x root/root  10711536 2012-11-29 05:17 ./usr/sbin/mysqld
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/man/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/man/man8/
-rw-r--r-- root/root      1703 2012-11-29 05:17 ./usr/share/man/man8/mysqld.8.gz
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/man/man1/
-rw-r--r-- root/root      5509 2012-11-29 05:17 ./usr/share/man/man1/myisampack.1.gz
-rw-r--r-- root/root      1634 2012-11-29 05:17 ./usr/share/man/man1/resolve_stack_dump.1.gz
-rw-r--r-- root/root      5465 2012-11-29 05:17 ./usr/share/man/man1/mysqld_safe.1.gz
-rw-r--r-- root/root      3760 2012-11-29 05:17 ./usr/share/man/man1/mysql_upgrade.1.gz
-rw-r--r-- root/root      1860 2012-11-29 05:17 ./usr/share/man/man1/mysql_tzinfo_to_sql.1.gz
-rw-r--r-- root/root      1819 2012-11-29 05:17 ./usr/share/man/man1/myisamlog.1.gz
-rw-r--r-- root/root      1461 2012-11-29 05:17 ./usr/share/man/man1/resolveip.1.gz
-rw-r--r-- root/root      2069 2012-11-29 05:17 ./usr/share/man/man1/mysql_convert_table_format.1.gz
-rw-r--r-- root/root      4991 2012-11-29 05:17 ./usr/share/man/man1/mysqltest.1.gz
-rw-r--r-- root/root      1664 2012-11-29 05:17 ./usr/share/man/man1/mysql_zap.1.gz
-rw-r--r-- root/root      2042 2012-11-29 05:17 ./usr/share/man/man1/comp_err.1.gz
-rw-r--r-- root/root     13510 2012-11-29 05:17 ./usr/share/man/man1/myisamchk.1.gz
-rw-r--r-- root/root      1871 2012-11-29 05:17 ./usr/share/man/man1/replace.1.gz
-rw-r--r-- root/root      1523 2012-11-29 05:17 ./usr/share/man/man1/msql2mysql.1.gz
-rw-r--r-- root/root     12172 2012-11-29 05:17 ./usr/share/man/man1/mysqlbinlog.1.gz
-rw-r--r-- root/root      2023 2012-11-29 05:17 ./usr/share/man/man1/mysql_setpermission.1.gz
-rw-r--r-- root/root      1582 2012-11-29 05:17 ./usr/share/man/man1/mysql_secure_installation.1.gz
-rw-r--r-- root/root      2733 2012-11-29 05:17 ./usr/share/man/man1/mysql_install_db.1.gz
-rw-r--r-- root/root      3317 2012-11-29 05:17 ./usr/share/man/man1/mysqlhotcopy.1.gz
-rw-r--r-- root/root      5342 2012-11-29 05:17 ./usr/share/man/man1/mysqld_multi.1.gz
-rw-r--r-- root/root      2133 2012-11-29 05:17 ./usr/share/man/man1/mysql.server.1.gz
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/doc/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/
-rw-r--r-- root/root     31424 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/myisam.txt
-rw-r--r-- root/root     17987 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/COPYING
-rw-r--r-- root/root  13619002 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/mysql.info
-rw-r--r-- root/root      2573 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/INFO_BIN
-rw-r--r-- root/root     19432 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/README-wsrep
-rw-r--r-- root/root       202 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/INFO_SRC
-rw-r--r-- root/root     63154 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/ChangeLog
-rw-r--r-- root/root      7604 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/INSTALL-BINARY
-rw-r--r-- root/root     41909 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/sp-imp-spec.txt
-rw-r--r-- root/root      2552 2012-11-29 05:17 ./usr/share/doc/mysql-server-5.5/README
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/
-rwxr-xr-x root/root      2605 2012-11-29 05:17 ./usr/share/mysql/debian-start.inc.sh
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/estonian/
-rw-r--r-- root/root     45073 2012-11-29 05:17 ./usr/share/mysql/estonian/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/norwegian-ny/
-rw-r--r-- root/root     44865 2012-11-29 05:17 ./usr/share/mysql/norwegian-ny/errmsg.sys
-rw-r--r-- root/root      1153 2012-11-29 05:17 ./usr/share/mysql/binary-configure
-rw-r--r-- root/root      3610 2012-11-29 05:17 ./usr/share/mysql/wsrep.cnf
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/norwegian/
-rw-r--r-- root/root     44811 2012-11-29 05:17 ./usr/share/mysql/norwegian/errmsg.sys
-rw-r--r-- root/root     59027 2012-11-29 05:17 ./usr/share/mysql/mysql_fix_privilege_tables.sql
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/slovak/
-rw-r--r-- root/root     45299 2012-11-29 05:17 ./usr/share/mysql/slovak/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/serbian/
-rw-r--r-- root/root     47254 2012-11-29 05:17 ./usr/share/mysql/serbian/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/german/
-rw-r--r-- root/root     52397 2012-11-29 05:17 ./usr/share/mysql/german/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/korean/
-rw-r--r-- root/root     47889 2012-11-29 05:17 ./usr/share/mysql/korean/errmsg.sys
-rw-r--r-- root/root      1626 2012-11-29 05:17 ./usr/share/mysql/config.small.ini
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/danish/
-rw-r--r-- root/root     45591 2012-11-29 05:17 ./usr/share/mysql/danish/errmsg.sys
-rw-r--r-- root/root      1061 2012-11-29 05:17 ./usr/share/mysql/mysqld_multi.server
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/hungarian/
-rw-r--r-- root/root     45449 2012-11-29 05:17 ./usr/share/mysql/hungarian/errmsg.sys
-rw-r--r-- root/root      2382 2012-11-29 05:17 ./usr/share/mysql/config.medium.ini
-rw-r--r-- root/root      2230 2012-11-29 05:17 ./usr/share/mysql/wsrep_notify
-rw-r--r-- root/root      1326 2012-11-29 05:17 ./usr/share/mysql/ndb-config-2-node.ini
-rw-r--r-- root/root     19783 2012-11-29 05:17 ./usr/share/mysql/my-innodb-heavy-4G.cnf
-rwxr-xr-x root/root        27 2012-11-29 05:17 ./usr/share/mysql/echo_stderr
-rw-r--r-- root/root      4675 2012-11-29 05:17 ./usr/share/mysql/my-large.cnf
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/english/
-rw-r--r-- root/root     44724 2012-11-29 05:17 ./usr/share/mysql/english/errmsg.sys
-rw-r--r-- root/root    470520 2012-11-29 05:17 ./usr/share/mysql/errmsg-utf8.txt
-rw-r--r-- root/root     28995 2012-11-29 05:17 ./usr/share/mysql/mysql_system_tables.sql
-rw-r--r-- root/root      4686 2012-11-29 05:17 ./usr/share/mysql/my-medium.cnf
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/italian/
-rw-r--r-- root/root     46611 2012-11-29 05:17 ./usr/share/mysql/italian/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/dutch/
-rw-r--r-- root/root     46591 2012-11-29 05:17 ./usr/share/mysql/dutch/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/greek/
-rw-r--r-- root/root     51537 2012-11-29 05:17 ./usr/share/mysql/greek/errmsg.sys
-rw-r--r-- root/root      3258 2012-11-29 05:17 ./usr/share/mysql/mysql_system_tables_data.sql
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/romanian/
-rw-r--r-- root/root     46547 2012-11-29 05:17 ./usr/share/mysql/romanian/errmsg.sys
-rw-r--r-- root/root      2850 2012-11-29 05:17 ./usr/share/mysql/my-small.cnf
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/charsets/
-rw-r--r-- root/root      5476 2012-11-29 05:17 ./usr/share/mysql/charsets/geostd8.xml
-rw-r--r-- root/root      5688 2012-11-29 05:17 ./usr/share/mysql/charsets/greek.xml
-rw-r--r-- root/root      5471 2012-11-29 05:17 ./usr/share/mysql/charsets/hebrew.xml
-rw-r--r-- root/root      5480 2012-11-29 05:17 ./usr/share/mysql/charsets/armscii8.xml
-rw-r--r-- root/root      5482 2012-11-29 05:17 ./usr/share/mysql/charsets/cp852.xml
-rw-r--r-- root/root      7192 2012-11-29 05:17 ./usr/share/mysql/charsets/latin2.xml
-rw-r--r-- root/root      7398 2012-11-29 05:17 ./usr/share/mysql/charsets/latin7.xml
-rw-r--r-- root/root      5462 2012-11-29 05:17 ./usr/share/mysql/charsets/hp8.xml
-rw-r--r-- root/root      5573 2012-11-29 05:17 ./usr/share/mysql/charsets/cp866.xml
-rw-r--r-- root/root      5489 2012-11-29 05:17 ./usr/share/mysql/charsets/keybcs2.xml
-rw-r--r-- root/root      6492 2012-11-29 05:17 ./usr/share/mysql/charsets/koi8u.xml
-rw-r--r-- root/root      5470 2012-11-29 05:17 ./usr/share/mysql/charsets/koi8r.xml
-rw-r--r-- root/root      8862 2012-11-29 05:17 ./usr/share/mysql/charsets/cp1257.xml
-rw-r--r-- root/root     17075 2012-11-29 05:17 ./usr/share/mysql/charsets/languages.html
-rw-r--r-- root/root     18312 2012-11-29 05:17 ./usr/share/mysql/charsets/Index.xml
-rw-r--r-- root/root      8195 2012-11-29 05:17 ./usr/share/mysql/charsets/cp1250.xml
-rw-r--r-- root/root      5466 2012-11-29 05:17 ./usr/share/mysql/charsets/ascii.xml
-rw-r--r-- root/root      5529 2012-11-29 05:17 ./usr/share/mysql/charsets/cp1256.xml
-rw-r--r-- root/root      5466 2012-11-29 05:17 ./usr/share/mysql/charsets/cp850.xml
-rw-r--r-- root/root      9770 2012-11-29 05:17 ./usr/share/mysql/charsets/latin1.xml
-rw-r--r-- root/root      8365 2012-11-29 05:17 ./usr/share/mysql/charsets/cp1251.xml
-rw-r--r-- root/root      6489 2012-11-29 05:17 ./usr/share/mysql/charsets/dec8.xml
-rw-r--r-- root/root      5469 2012-11-29 05:17 ./usr/share/mysql/charsets/latin5.xml
-rw-r--r-- root/root      1749 2012-11-29 05:17 ./usr/share/mysql/charsets/README
-rw-r--r-- root/root      6490 2012-11-29 05:17 ./usr/share/mysql/charsets/swe7.xml
-rw-r--r-- root/root      8007 2012-11-29 05:17 ./usr/share/mysql/charsets/macce.xml
-rw-r--r-- root/root      8018 2012-11-29 05:17 ./usr/share/mysql/charsets/macroman.xml
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/swedish/
-rw-r--r-- root/root     45628 2012-11-29 05:17 ./usr/share/mysql/swedish/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/ukrainian/
-rw-r--r-- root/root     54831 2012-11-29 05:17 ./usr/share/mysql/ukrainian/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/french/
-rw-r--r-- root/root     46225 2012-11-29 05:17 ./usr/share/mysql/french/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/japanese/
-rw-r--r-- root/root     46758 2012-11-29 05:17 ./usr/share/mysql/japanese/errmsg.sys
-rw-r--r-- root/root     30032 2012-11-29 05:17 ./usr/share/mysql/mysql_system_tables_fix.sql
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/czech/
-rw-r--r-- root/root     46138 2012-11-29 05:17 ./usr/share/mysql/czech/errmsg.sys
-rw-r--r-- root/root      4701 2012-11-29 05:17 ./usr/share/mysql/my-huge.cnf
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/spanish/
-rw-r--r-- root/root     46455 2012-11-29 05:17 ./usr/share/mysql/spanish/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/russian/
-rw-r--r-- root/root     60307 2012-11-29 05:17 ./usr/share/mysql/russian/errmsg.sys
-rw-r--r-- root/root     10371 2012-11-29 05:17 ./usr/share/mysql/mysql_test_data_timezone.sql
-rwxr-xr-x root/root     10585 2012-11-29 05:17 ./usr/share/mysql/mysql.server
-rw-r--r-- root/root    628991 2012-11-29 05:17 ./usr/share/mysql/fill_help_tables.sql
-rw-r--r-- root/root       789 2012-11-29 05:17 ./usr/share/mysql/mysql-log-rotate
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/polish/
-rw-r--r-- root/root     45433 2012-11-29 05:17 ./usr/share/mysql/polish/errmsg.sys
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/share/mysql/portuguese/
-rw-r--r-- root/root     47815 2012-11-29 05:17 ./usr/share/mysql/portuguese/errmsg.sys
-rw-r--r-- root/root      4528 2012-11-29 05:17 ./usr/share/mysql/config.huge.ini
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/lib/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/lib/mysql/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/lib/mysql/plugin/
drwxr-xr-x root/root         0 2012-11-29 05:17 ./usr/bin/
-rwxr-xr-x root/root   3536920 2012-11-29 05:17 ./usr/bin/mysqltest
-rwxr-xr-x root/root      1412 2012-11-29 05:17 ./usr/bin/msql2mysql
-rwxr-xr-x root/root      8198 2012-11-29 05:17 ./usr/bin/mysql_secure_installation
-rwxr-xr-x root/root   2827416 2012-11-29 05:17 ./usr/bin/my_print_defaults_wsrep
-rwxr-xr-x root/root   3437760 2012-11-29 05:17 ./usr/bin/mysqlbinlog
-rwxr-xr-x root/root   3151704 2012-11-29 05:17 ./usr/bin/myisampack
-rwxr-xr-x root/root      4245 2012-11-29 05:17 ./usr/bin/mysql_convert_table_format
-rwxr-xr-x root/root     17473 2012-11-29 05:17 ./usr/bin/mysql_setpermission
-rwxr-xr-x root/root   2800760 2012-11-29 05:17 ./usr/bin/mysql_tzinfo_to_sql
-rwxr-xr-x root/root      4899 2012-11-29 05:17 ./usr/bin/wsrep_sst_mysqldump
-rwxr-xr-x root/root     25647 2012-11-29 05:17 ./usr/bin/mysqld_safe
-rwxr-xr-x root/root   3111256 2012-11-29 05:17 ./usr/bin/myisamlog
-rwxr-xr-x root/root     34852 2012-11-29 05:17 ./usr/bin/mysqlhotcopy
-rwxr-xr-x root/root   2812760 2012-11-29 05:17 ./usr/bin/replace
-rwxr-xr-x root/root   2903328 2012-11-29 05:17 ./usr/bin/mysql_upgrade
-rwxr-xr-x root/root   2827352 2012-11-29 05:17 ./usr/bin/resolve_stack_dump
-rwxr-xr-x root/root     14849 2012-11-29 05:17 ./usr/bin/mysql_install_db
-rwxr-xr-x root/root   3234040 2012-11-29 05:17 ./usr/bin/myisamchk
-rwxr-xr-x root/root      6110 2012-11-29 05:17 ./usr/bin/wsrep_sst_xtrabackup
-rwxr-xr-x root/root      3888 2012-11-29 05:17 ./usr/bin/mysql_zap
-rwxr-xr-x root/root      5616 2012-11-29 05:17 ./usr/bin/wsrep_sst_rsync
-rwxr-xr-x root/root   2826168 2012-11-29 05:17 ./usr/bin/resolveip
-rwxr-xr-x root/root      2467 2012-11-29 05:17 ./usr/bin/wsrep_sst_common
-rwxr-xr-x root/root     23199 2012-11-29 05:17 ./usr/bin/mysqld_multi
lrwxrwxrwx root/root         0 2012-11-29 05:17 ./usr/bin/wsrep_sst_rsync_wan -> wsrep_sst_rsync
tiennv000@td:~/Downloads$
 ````
  
#### 5. Kiểm tra một gói đã được cài đặt hay chưa
  Sử dụng tùy chọn "-s" và tên gói để xem gói ".deb" đã được cài đặt chưa.
 ``` 
    dpkg -s mysql-server-wsrep
 ```	
 ````
tiennv000@td:~/Downloads$ dpkg -s mysql-server-wsrep
Package: mysql-server-wsrep
Status: install ok unpacked
Maintainer: Codership Oy
Architecture: amd64
Version: 5.5.28-23.7
Replaces: mysql-server-core (<= 5.5.28), mysql-server-core-5.0 (<= 5.5.28), mysql-server-core-5.1 (<= 5.5.28), mysql-server (<= 5.5.28), mysql-server-5.0 (<= 5.5.28), mysql-server-5.1 (<= 5.5.28), mysql-server-core-5.5 (<= 5.5.28), mysql-server-5.5 (<= 5.5.28)
Provides: mysql-server-core, mysql-server, mysql-server-core-5.5, mysql-server-5.5
Depends: psmisc, debianutils (>= 1.6), libc6 (>= 2.4), libdbi-perl, libdbd-mysql-perl (>= 1.2202), libgcc1 (>= 4.1.1), libncurses5 (>= 5.6), libstdc++6 (>= 4.1.1), libwrap0 (>= 7.6), perl, zlib1g (>= 1.1.4), libaio1, mysql-client
Conffiles:
 /etc/mysql/conf.d/wsrep.cnf newconffile
Description: wsrep-enabled MySQL server
 Copyright: MySQL AB, Codership Oy, All Rights Reserved
 MySQL server + wsrep patch (https://launchpad.net/codership-mysql)
tiennv000@td:~/Downloads$ 

 ````
 
#### 6. Kiểm tra vị trí của gói đã được cài đặt
  Hiển thị vị trí các file trong hệ thống của gói đã cài đặt theo tên của gói. Dùng lệnh với tùy chọn "-L"
 ```
    dpkg -L mysql-server-wsrep
 ```
 ````
tiennv000@td:~/Downloads$     dpkg -L mysql-server-wsrep
/.
/etc
/etc/logrotate.d
/etc/logrotate.d/mysql-server
/etc/init.d
/etc/init.d/mysql
/etc/logcheck
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/mysql-server-5_5
/etc/logcheck/ignore.d.workstation
/etc/logcheck/ignore.d.workstation/mysql-server-5_5
/etc/logcheck/ignore.d.paranoid
/etc/logcheck/ignore.d.paranoid/mysql-server-5_5
/etc/mysql
/etc/mysql/debian-start
/etc/mysql/conf.d
/etc/mysql/conf.d/wsrep.cnf
/etc/mysql/conf.d/mysqld_safe_syslog.cnf
/var
/var/run
/var/run/mysqld
/usr
/usr/sbin
/usr/sbin/mysqld
/usr/share
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/mysqld.8.gz
/usr/share/man/man1
/usr/share/man/man1/myisampack.1.gz
/usr/share/man/man1/resolve_stack_dump.1.gz
/usr/share/man/man1/mysqld_safe.1.gz
/usr/share/man/man1/mysql_upgrade.1.gz
/usr/share/man/man1/mysql_tzinfo_to_sql.1.gz
/usr/share/man/man1/myisamlog.1.gz
/usr/share/man/man1/resolveip.1.gz
/usr/share/man/man1/mysql_convert_table_format.1.gz
/usr/share/man/man1/mysqltest.1.gz
/usr/share/man/man1/mysql_zap.1.gz
/usr/share/man/man1/comp_err.1.gz
/usr/share/man/man1/myisamchk.1.gz
/usr/share/man/man1/replace.1.gz
/usr/share/man/man1/msql2mysql.1.gz
/usr/share/man/man1/mysqlbinlog.1.gz
/usr/share/man/man1/mysql_setpermission.1.gz
/usr/share/man/man1/mysql_secure_installation.1.gz
/usr/share/man/man1/mysql_install_db.1.gz
/usr/share/man/man1/mysqlhotcopy.1.gz
/usr/share/man/man1/mysqld_multi.1.gz
/usr/share/man/man1/mysql.server.1.gz
/usr/share/doc
/usr/share/doc/mysql-server-5.5
/usr/share/doc/mysql-server-5.5/myisam.txt
/usr/share/doc/mysql-server-5.5/COPYING
/usr/share/doc/mysql-server-5.5/mysql.info
/usr/share/doc/mysql-server-5.5/INFO_BIN
/usr/share/doc/mysql-server-5.5/README-wsrep
/usr/share/doc/mysql-server-5.5/INFO_SRC
/usr/share/doc/mysql-server-5.5/ChangeLog
/usr/share/doc/mysql-server-5.5/INSTALL-BINARY
/usr/share/doc/mysql-server-5.5/sp-imp-spec.txt
/usr/share/doc/mysql-server-5.5/README
/usr/share/mysql
/usr/share/mysql/debian-start.inc.sh
/usr/share/mysql/estonian
/usr/share/mysql/estonian/errmsg.sys
/usr/share/mysql/norwegian-ny
/usr/share/mysql/norwegian-ny/errmsg.sys
/usr/share/mysql/binary-configure
/usr/share/mysql/wsrep.cnf
/usr/share/mysql/norwegian
/usr/share/mysql/norwegian/errmsg.sys
/usr/share/mysql/mysql_fix_privilege_tables.sql
/usr/share/mysql/slovak
/usr/share/mysql/slovak/errmsg.sys
/usr/share/mysql/serbian
/usr/share/mysql/serbian/errmsg.sys
/usr/share/mysql/german
/usr/share/mysql/german/errmsg.sys
/usr/share/mysql/korean
/usr/share/mysql/korean/errmsg.sys
/usr/share/mysql/config.small.ini
/usr/share/mysql/danish
/usr/share/mysql/danish/errmsg.sys
/usr/share/mysql/mysqld_multi.server
/usr/share/mysql/hungarian
/usr/share/mysql/hungarian/errmsg.sys
/usr/share/mysql/config.medium.ini
/usr/share/mysql/wsrep_notify
/usr/share/mysql/ndb-config-2-node.ini
/usr/share/mysql/my-innodb-heavy-4G.cnf
/usr/share/mysql/echo_stderr
/usr/share/mysql/my-large.cnf
/usr/share/mysql/english
/usr/share/mysql/english/errmsg.sys
/usr/share/mysql/errmsg-utf8.txt
/usr/share/mysql/mysql_system_tables.sql
/usr/share/mysql/my-medium.cnf
/usr/share/mysql/italian
/usr/share/mysql/italian/errmsg.sys
/usr/share/mysql/dutch
/usr/share/mysql/dutch/errmsg.sys
/usr/share/mysql/greek
/usr/share/mysql/greek/errmsg.sys
/usr/share/mysql/mysql_system_tables_data.sql
/usr/share/mysql/romanian
/usr/share/mysql/romanian/errmsg.sys
/usr/share/mysql/my-small.cnf
/usr/share/mysql/charsets
/usr/share/mysql/charsets/geostd8.xml
/usr/share/mysql/charsets/greek.xml
/usr/share/mysql/charsets/hebrew.xml
/usr/share/mysql/charsets/armscii8.xml
/usr/share/mysql/charsets/cp852.xml
/usr/share/mysql/charsets/latin2.xml
/usr/share/mysql/charsets/latin7.xml
/usr/share/mysql/charsets/hp8.xml
/usr/share/mysql/charsets/cp866.xml
/usr/share/mysql/charsets/keybcs2.xml
/usr/share/mysql/charsets/koi8u.xml
/usr/share/mysql/charsets/koi8r.xml
/usr/share/mysql/charsets/cp1257.xml
/usr/share/mysql/charsets/languages.html
/usr/share/mysql/charsets/Index.xml
/usr/share/mysql/charsets/cp1250.xml
/usr/share/mysql/charsets/ascii.xml
/usr/share/mysql/charsets/cp1256.xml
/usr/share/mysql/charsets/cp850.xml
/usr/share/mysql/charsets/latin1.xml
/usr/share/mysql/charsets/cp1251.xml
/usr/share/mysql/charsets/dec8.xml
/usr/share/mysql/charsets/latin5.xml
/usr/share/mysql/charsets/README
/usr/share/mysql/charsets/swe7.xml
/usr/share/mysql/charsets/macce.xml
/usr/share/mysql/charsets/macroman.xml
/usr/share/mysql/swedish
/usr/share/mysql/swedish/errmsg.sys
/usr/share/mysql/ukrainian
/usr/share/mysql/ukrainian/errmsg.sys
/usr/share/mysql/french
/usr/share/mysql/french/errmsg.sys
/usr/share/mysql/japanese
/usr/share/mysql/japanese/errmsg.sys
/usr/share/mysql/mysql_system_tables_fix.sql
/usr/share/mysql/czech
/usr/share/mysql/czech/errmsg.sys
/usr/share/mysql/my-huge.cnf
/usr/share/mysql/spanish
/usr/share/mysql/spanish/errmsg.sys
/usr/share/mysql/russian
/usr/share/mysql/russian/errmsg.sys
/usr/share/mysql/mysql_test_data_timezone.sql
/usr/share/mysql/mysql.server
/usr/share/mysql/fill_help_tables.sql
/usr/share/mysql/mysql-log-rotate
/usr/share/mysql/polish
/usr/share/mysql/polish/errmsg.sys
/usr/share/mysql/portuguese
/usr/share/mysql/portuguese/errmsg.sys
/usr/share/mysql/config.huge.ini
/usr/lib
/usr/lib/mysql
/usr/lib/mysql/plugin
/usr/bin
/usr/bin/mysqltest
/usr/bin/msql2mysql
/usr/bin/mysql_secure_installation
/usr/bin/my_print_defaults_wsrep
/usr/bin/mysqlbinlog
/usr/bin/myisampack
/usr/bin/mysql_convert_table_format
/usr/bin/mysql_setpermission
/usr/bin/mysql_tzinfo_to_sql
/usr/bin/wsrep_sst_mysqldump
/usr/bin/mysqld_safe
/usr/bin/myisamlog
/usr/bin/mysqlhotcopy
/usr/bin/replace
/usr/bin/mysql_upgrade
/usr/bin/resolve_stack_dump
/usr/bin/mysql_install_db
/usr/bin/myisamchk
/usr/bin/wsrep_sst_xtrabackup
/usr/bin/mysql_zap
/usr/bin/wsrep_sst_rsync
/usr/bin/resolveip
/usr/bin/wsrep_sst_common
/usr/bin/mysqld_multi
/usr/bin/wsrep_sst_rsync_wan
tiennv000@td:~/Downloads$ 

 ````
  
#### 7. Cài đặt tất các các gói trong một thư mục
  Cài đặt tất cả các gói phù hợp với định dạng "*.deb" được tìm thấy trong một thư mục hoặc các thư mục con. Sử dụng tùy chọn "-R" và "--install".

    dpkg -R --install testdeb/
	
  Hoặc cũng có thể làm theo cách khác. Lưu hết các gói dạng ".deb" vào một thư mục, cd vào thư mục và chạy lệnh.
  
    dpkg -i *.deb
	
#### 8. Giải nén các gói mà không cấu hình
  Sử dụng "-unpack" để giải nén gói nhưng không cài đặt hay cấu hình gói.
 ```
    dpkg --unpack mysql-server-wsrep-5.5.28-23.7-amd64.deb
 ```
 ````
tiennv000@td:~/Downloads$ sudo dpkg --unpack mysql-server-wsrep-5.5.28-23.7-amd64.deb
[sudo] password for tiennv000: 
(Reading database ... 213593 files and directories currently installed.)
Preparing to unpack mysql-server-wsrep-5.5.28-23.7-amd64.deb ...
Unpacking mysql-server-wsrep (5.5.28-23.7) over (5.5.28-23.7) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
tiennv000@td:~/Downloads$ 
 ````
	
#### 9. Cấu hình lại một gói đã giải nén
  Dùng tùy chọn "-configure" để cấu hình lại một gói đã được giải nén
  
    dpkg --configure mysql-server-wsrep
	
#### 10. Thay thế thông tin của gói
  Dùng tùy chọn "--update-avail" thay thế các thông tin cũ với các thông tin có sãn trong tập tin gói.
  
    dpkg –-update-avail mysql-server-wsrep-5.5.28-23.7-amd64.deb
	
#### 11. Xóa bỏ thông tin có sẵn của gói
  Dùng "-clear-avaial" sẽ xóa những thông tin hiện tại sẵn có của các gói
  
    dpkg –-clear-avail
	
#### 12. Hiển thị thông tin phiên bản dpkg
  "--version" sẽ hiển thị thông tin phiên bản của dpkg
  
    dpkg --version
	
 ```
tiennv000@td:~/Downloads$     dpkg --version
Debian 'dpkg' package management program version 1.18.4 (amd64).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.
tiennv000@td:~/Downloads$ 
 ```
  
#### 13. Nhận các trợ giúp về dpkg
  "--help" sẽ hiển thị danh sách các tùy chọn của lệnh dpkg
  
    dpkg –-help
	
  
#### 14. Hiển thị Licence dpkg

    
#### 15. Forget Uninstalled and Unavailable Packages

