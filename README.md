# https://admin.yandex.ru/

Управляем пользователями почты через ansible

## Requirements

Потребуется создать токен для доступа и занести его в файл `roles/imbicile.yandex/defaults/main.yml` вместе с именем домена

## Role Variables

Основная информация по api https://yandex.ru/dev/pdd/doc/concepts/termin.html

## Пример Playbook

Создадим 2х `newuser_1 \ newuser_2`пользователей и 2х удалим `newuser_3 \ newuser_4`

```yml
---
- hosts: 127.0.0.1
  connection: local

  vars:
    yandex_user_add:
      - login: "newuser_1"
        password: "H@rdp@ZZw0rd"
        iname: "Имя_1"
        fname: "Фамилия_1"
        enabled: "yes"
        birth_date: "2000-12-03"
        sex: "1"
        hintq: "Ты знаешь путь ?"
        hinta: "Клац клац !"

      - login: "newuser_2"
        password: "H@rdp@ZZw0rd"
        iname: "Имя_2"
        fname: "Фамилия_2"
        enabled: "yes"
        birth_date: "2004-11-09"
        sex: "2"
        hintq: "Во славу ?"
        hinta: "Льдистого чертога !"

    yandex_user_del:
      - login: "newuser_3"
        status: "absent"
      - login: "newuser_4"
        status: "absent"
  roles:
    - role: imbicile.yandex
      tags: yandex
```
