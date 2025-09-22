# SSH

Настройки подключений:

```bash

/etc/ssh/sshd_config
/etc/ssh/sshd_config.d/*.conf

```

Проверить установлен ли SSH-ключ для текущего пользователя:

```bash
ls ~/.ssh
```

Наименования ключей? id_rsa и id_rsa.pub

Создание SSH-ключа:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

где, -t rsa - использовать алгоритм RSA. -b - количество битов. -C - комментарий

Добавить SSH-ключ в ssh-agent:

```bash

eval $(ssh-agent -s)
ssh-add ~/.ssh/id_rsa

```

Проверить подключение ключа к определенному сервису:

```bash
ssh -T git@github.com
```

## Добавить ключ в GitHub

        * Перейти на GitHub
        * Настройки -> SSH and GPG keys -> New SSH key
        * Вставить ключ id_rsa.pub
