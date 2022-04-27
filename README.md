# Установка Webmin и BitrixEnv

Установка панели управления хостингом и окружения Битрикс.

После запуска виртуальной машины на ней уже будет установлен Webmin.
Необходимо установить bitrixenv:

    1. подключиться к виртуальной машине и запустить
    скрипт установки окружения Битрикс:

    vagrant ssh
    sudo -i
    ./bitrix-env.sh

    2. в меню управления виртуальной машиной создать pool

    3. в браузере продолжить установку CMS Битрикс
    http://127.0.0.1:8080

    4. Открыть порт 10000 для Webmin

    iptables -I INPUT -p tcp --dport 10000 -j ACCEPT
    service iptables save

Доступ к Webmin http://127.0.0.1:10000

user: root  
pass: root

## Ссылки

[Установка «1С-Битрикс: Веб-окружение» - Linux (BitrixEnv)](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=37&LESSON_ID=8811)
