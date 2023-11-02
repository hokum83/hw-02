# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Гультяев Алексей`

### Задание 1
Авторизация в админке:
![Авторизация в админке](https://github.com/hokum83/8-02/blob/main/img/8-02-1-1.png)

Главный экран:
![Главный экран](https://github.com/hokum83/8-02/blob/main/img/8-02-1-2.png)

Код:
```
sudo su
apt install postgresql
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-5+debian12_all.deb
dpkg -i ./zabbix-release_6.0-5+debian12_all.deb 
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
nano /etc/zabbix/zabbix_server.conf
systemctl restart zabbix-server apache2
systemctl enable zabbix-server apache2
```


### Задание 2
Раздел Hosts:
![Раздел Hosts:](https://github.com/hokum83/8-02/blob/main/img/8-02-2-1.png)

Логи агента:
![Логи агента](https://github.com/hokum83/8-02/blob/main/img/8-02-2-2.png)

Раздел Latest Data:
![Раздел Latest Data](https://github.com/hokum83/8-02/blob/main/img/8-02-2-2.png)

Код:
```
sudo su
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-5+debian12_all.deb
dpkg -i ./zabbix-release_6.0-5+debian12_all.deb 
apt update
apt install zabbix-agent
nano /etc/zabbix/zabbix_agentd.conf 
systemctl restart zabbix-agent
systemctl enable zabbix-agent
```