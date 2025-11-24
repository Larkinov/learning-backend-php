# SSH

Настройки подключений:

```bash

/etc/ssh/sshd_config
/etc/ssh/sshd_config.d/*.conf

```

Каталог хранения ключей на сервере:

```bash
/home/username/.ssh/authorized_keys - для username
/root/.ssh/authorized_keys - для рута
```
Каталог хранения ключей на локальной машине (windows):
```
/c/username/.ssh
```

Стандартные наименования ключей при их генерации:
```
id_rsa - закрытый
id_rsa.pub - открытый
```

Создание SSH-ключа:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

где, -t rsa - использовать алгоритм RSA. -b - количество битов. -C - комментарий


Проверить подключение ключа к определенному сервису:

```bash
ssh -T git@github.com
```

## Добавить ключ в GitHub

        * Перейти на GitHub
        * Настройки -> SSH and GPG keys -> New SSH key
        * Вставить ключ id_rsa.pub


## Putty
Чтобы получить закрытый ключ в формате OpenSSL: конвертировать->экспортировать в формате OpenSSL