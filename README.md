# zabbix-selinux

$ setsebool -P httpd_can_connect_zabbix 1
$ setsebool -P zabbix_can_network 1
$ grep "denied.*zabbix" /var/log/audit/audit.log | audit2allow -M zabbix_custom_policy
$ semodule -i zabbix_custom_policy.pp
$ grep "denied.*php-fpm" /var/log/audit/audit.log | audit2allow -M php-fpm_custom_policy
$ semodule -i php-fpm_custom_policy.pp
$ reboot
