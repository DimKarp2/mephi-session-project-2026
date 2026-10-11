# MEPHI Session Project 2026

Сессионный проект по настройке базовых средств защиты **РЕД ОС 8**.

## Выполненные разделы

| Раздел | Краткое описание | Основные артефакты |
|---|---|---|
| 1. Установка и сеть | Настроены DHCP, hostname `mephi-2026.domain.local`, проверена внешняя связность | `ping.out`, `history.out` |
| 2. Управление ПО | Обновлена система, установлены `nginx`, `libcap-ng-utils`, `tcpdump` установлен из локального RPM | `dnf.out`, `history.out` |
| 3. Файловые системы | Второй диск размечен и отформатирован в ext4 с меткой `MEPHI_WEB`, настроено автомонтирование в `/mephi-web` | `fstab`, `history.out` |
| 4. Сервисы | `nginx` запущен и включён в автозагрузку, сохранён журнал текущей загрузки | `journalctl.out` |
| 5. Управление доступом | Настроены пользователи и ACL для `/data/mephi-2026`, capabilities для `tcpdump`, SELinux для `/mephi-web` | `passwd`, `group`, `stat.out`, `getcap.out`, `getenforce.out`, `history.out` |
| 6. Аутентификация | Кураторам запрещён интерактивный вход, срок действия пароля установлен в 90 дней, минимальная длина — 12 символов | `passwd`, `shadow`, `pwquality.conf`, `history.out` |
| 7. Тестирование | `nginx` отдаёт страницу из `/mephi-web` с номером студента | `curl.out`, `mephi-screenshot.png` |
| 8. Публикация | Артефакты опубликованы в публичном GitHub-репозитории | все файлы репозитория |

## Ключевой результат

```text
Hello from Student: M265859
```

`nginx` обслуживает контент из нестандартной директории `/mephi-web`, SELinux работает в режиме `Enforcing`, а для каталога используется тип `httpd_sys_content_t`.

## Артефакты

- `mephi-screenshot.png` — визуальное подтверждение результата
- `history.out` — история команд
- `ping.out` — проверка сетевой связности
- `dnf.out` — история транзакций DNF
- `stat.out` — права и SELinux-контексты каталогов
- `journalctl.out` — журнал nginx
- `getcap.out` — capabilities `tcpdump`
- `getenforce.out` — режим SELinux
- `curl.out` — результат проверки web-сервера
- `fstab` — автоматическое монтирование `/mephi-web`
- `passwd`, `shadow`, `group` — пользователи, группы и парольная политика
- `pwquality.conf` — минимальная длина пароля
