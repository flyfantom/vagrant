# Стенд с кластером CEPH

## Описание стенда



### Схема стенда

![scheme_current.png](scheme/scheme_current.png)

### Описание серверов

<details><summary>Описанием серверов (нажать, чтобы открыть)</summary><p>

| server                       | ip-адрес                                                 | функциональная роль                                          | ключевое используемое ПО                                     | комментарий                                                  |
| ---------------------------- | -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ceph-lab-client              | 10.11.0.5, 172.16.21.5                                   | точка входа web-клиентов, источник http-трафика для нагрузочного тестирования | docker, yandex.tank                                          | для использования сервиса [Overload𝛃](https://overload.yandex.net/) требуется создать свой файл с токеном |
| ceph-lab-1                   | 10.11.0.10, 172.16.21.10                                 | балансировщик http-трафика, master keepalived                | haproxy, keepalived                                          |                                                              |
| ceph-lab-2                   | 10.11.0.20, 172.16.21.20                                 | балансировщик http-трафика, backup keepalived                | haproxy, keepalived                                          |                                                              |
| ceph-lab-3                   | 10.11.0.30, 172.16.21.30                                 | активный web-сервер фронтенда zabbix, бэкенд (zabbix-server) с VIP-адресом, мониторинг параметров БД текущего лидера в кластере postresql | nginx, php-fpm, zabbix-server-pgsql, zabbix-web-pgsql, mamonsu, pacemaker |                                                              |
| ceph-lab-4                   | 10.11.0.40, 172.16.21.40                                 | активный web-сервер фронтенда zabbix, бэкенд (zabbix-server) с VIP-адресом, мониторинг параметров БД текущего лидера в кластере postresql, репозиторий mamonsu | nginx, php-fpm, zabbix-server-pgsql, zabbix-web-pgsql, mamonsu, pacemaker |                                                              |
</p></details>
