# SYSTEMD

Systemd - менеджер служб

## systemd

Каталог служб
```
/etc/systemd/system
```

Пример конфигурации службы-воркера
```
[Unit]
Description=ОПИСАНИЕ
After=ПОСЛЕ КАКОЙ СЛУЖБЫ ЗАПУСКАТЬ ТЕКУЩУЮ

[Service]
Type=simple (сервис считается запущенным простым выполнением команды ExecStart)
ExecStart=КОМАНДА ЗАПУСКА
Restart=ТИП РЕСТАРТА
RestartSec=ВРЕМЯ РЕСТАРТА
User=ПОЛЬЗОВАТЕЛЬ
Group=ГРУППА
WorkingDirectory=РАБОЧАЯ ДИРЕКТОРИЯ

# СТАНДАРТНЫЕ ЛОГИ (В journalctl)
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target (при каких условиях запускать службу; стандартная цель)

```

## systemctl


Автоматический запуск/отключение службы при загрузке
```bash
systemctl enable/disable SERVICE_NAME
```

Посмотреть все службы
```bash
systemctl list-units --type=service
```

Обновить конфигурации без перезапуска самих служб
```bash
systemctl daemon-reload
```

Очистка состояния провальных и/или не найденных служб
```bash
systemctl reset-failed
```

Статус службы
```bash
systemctl status SERVICE_NAME
```

## journalctl

Последние логи службы (конец файла)
```bash
journalctl -u SERVICE_NAME -e
```

