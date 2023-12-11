Reverse proxy-role
=========

Ansible role для настройки Nginx reverse proxy.
Состоит из следующих действий:
- Установка сервера nginx, certbot - [install.yml](https://github.com/roman-serdyukov/reverse-proxy-role/blob/main/tasks/install.yml).
- Копирование конфигурации nginx.conf, файлов конфигурации для сайтов (sites-available) - [proxy.yml](https://github.com/roman-serdyukov/reverse-proxy-role/blob/main/tasks/proxy.yml).
- Копирование файлов конфигурации для переадресации портов на внутренние хосты (stream-available) - [stream.yml](https://github.com/roman-serdyukov/reverse-proxy-role/blob/main/tasks/stream.yml).
- Получение сертификатов - [certificate.yml](https://github.com/roman-serdyukov/reverse-proxy-role/blob/main/tasks/certificate.yml).

Requirements
------------

Работоспособность протестирована на Ubuntu 20.04 и Ubuntu 18.04.


Role Variables
--------------

- domain_zones: список поддоменов для копирования конфигураций сайтов, а также для получения сетрификатов.
- domain_streams: список поддоменов для копирования конфигураций для переадресации портов на внутренние хосты.
- my_domain: доменное имя.
- email - адрес электронной почты для cerbot
- IP адреса внутренних хостов.
- порты используемых служб.
- внешние порты для переадресации.

Example Playbook
----------------
```
- name: Install reverse proxy
  hosts: servers
  roles:
    - reverse-proxy-nginx
```

Before start
----------------

- Если нет внутрненнего DNS сервера, то раскоментировать копирование файла hosts в секции proxy.yml.
- Для Product сервера изменить команду получения сертификатов в certificate.yml (выбрать без параметра --test-cert).

License
-------

MIT

Author Information
------------------

Сердюков Роман
reserdukov@gmail.com