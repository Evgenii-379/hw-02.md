
# **Тема: "Система мониторинга, Zabbix"** - ***Вуколов Евгений***

## **Задание 1**

- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-16%20225339.png)
- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-16%20225410.png)

- sudo -su
- apt update
- apt upgrade
- apt install postgresql
- wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
- dpkg -i zabbix-release_6.0-4+debian11_all.deb
- apt update
- apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts 
- su -postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD'\'123456789\'';"'
- su -postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
- zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
- sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf
- systemctl restart zabbix-server apache2
- systemctl enable zabbix-server apache2
- systemctl status zabbix-server


## **Задание 2**

- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-17%20174515.png)
- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-17%20200917.png)
- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-17%20200704.png)
- ![scrinshot](https://github.com/Evgenii-379/hw-02.md/blob/main/Снимок%20экрана%202024-01-17%20200717.png)

- sudo su -
- apt update
- apt upgrade
- wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
- dpkg -i zabbix-release_6.0-4+debian11_all.deb
- apt install zabbix-agent
- sed -i 's/Server=127.0.0.1/Server=51.250.123.169/g' /etc/zabbix/zabbix_agentd.conf
- systemctl restart zabbix-agent
- systemctl enable zabbix-agent
- systemctl status zabbix-agent
