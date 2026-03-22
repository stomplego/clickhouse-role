# Ansible Role: ClickHouse

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-clickhouse--role-blue.svg)](https://galaxy.ansible.com/stomple/clickhouse-role)

## Описание

Роль для установки и базовой настройки ClickHouse.

## Требования

- Ansible >= 2.9
- Ubuntu 20.04 / 22.04 / 24.04
- Минимум 800 МБ свободного места

## Переменные роли

| Имя | Значение по умолчанию | Описание |
|-----|----------------------|----------|
| `clickhouse_version` | `26.4.1.109` | Версия ClickHouse |
| `clickhouse_user` | `clickhouse` | Системный пользователь |
| `clickhouse_http_port` | `8123` | HTTP API порт |
| `clickhouse_data_dir` | `/var/lib/clickhouse` | Директория данных |

## Пример playbook

### Базовая установка

```yaml
---
- name: Установка ClickHouse
  hosts: all
  become: yes
  roles:
    - role: stomple.clickhouse-role


### Переопределение переменных

Если нужно изменить порт или директорию данных:

```yaml
- hosts: clickhouse_servers
  roles:
    - role: clickhouse-role
      vars:
        clickhouse_data_dir: /mnt/clickhouse/data
        clickhouse_http_port: 8124
        clickhouse_version: "25.1.1.123"
