# command-dpkg
command-dpkg
=====
# Giới thiệu về dpkg
DPKG là chương trình chính quản lí gói trong Debian. Nó sử dụng để install, build, remove, và manage các gói. Aptitude là front-end chính cho dpkg.
Dưới đây một số lệnh dpkg thường được sử dụng.
### 1. Cài đặt gói
Để cài đặt một gói ".deb", sử dụng lệnh với tùy chọn "-i". Ví dụ để cài đặt một gói ".deb" như "mysql-server-wsrep-5.5.28-23.7-amd64.deb" sử dụng lệnh sau đây.
 ```
	dpkg -i mysql-server-wsrep-5.5.28-23.7-amd64.deb
 ```
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
