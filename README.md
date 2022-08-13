Reverse proxy-role
=========

Ansible role для настройки Nginx reverse proxy.
Состоит из следующих действий:
- Установка сервера nginx, certbot - install.yml.
- Копирование конфигурации nginx.conf, файлов конфигурации для сайтов (sites-available) - proxy.yml.
- Копирование файлов конфигурации для переадресации портов на внутренние хосты (stream-available) - stream.yml.
- Получение сертификатов - certificate.yml.

Requirements
------------

Работоспособность протестирована на Ubuntu 20.04 и Ubuntu 18.04.


Role Variables
--------------

- domain_zones: список поддоменов для копирования конфигураций сайтов, а также для получения сетрификатов.
- domain_streams: список поддоменов для копирования конфигураций для переадресации портов на внутренние хосты.
- my_domain: доменное имя.
- IP адреса внутренних хостов.
- порты используемых служб.
- внешние порты для переадресации.

Example Playbook
----------------
```
- name: Install reverse proxy
  hosts: servers
      roles:
         - { role: reverse-proxy-nginx, when: ansible_lsb.id == 'Ubuntu' }
```

Before start
----------------

- Если нет внутрненнего DNS сервера, то раскоментировать копирование файла hosts в секции proxy.yml.
- Для "боевого" сервера изменить команду получения сертификатов в certificate.yml (выбрать без параметра --test-cert).

License
-------

MIT

Author Information
------------------

Сердюков Роман
reserdukov@gmail.com