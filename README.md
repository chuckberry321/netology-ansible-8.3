# 08.03 Использование Yandex Cloud

Установка ELK cтека на виртуальных машинах Yandex Cloud.   
Каждый компонент устанавливается на отдельную виртуальную машину.   
Адреса машин указываются в inventory/prod/hosts.yml.   
Версия  ELK стека определяется переменной elk_stack_version в соответствующих файлах в inventory/prod/group_vars/.   
Подключение к хостам осуществляется по ssh.   

Запуск playbook
```
ansible-playbook -i inventory/prod/ site.yml
```

Структура каждого playbook:   
- хендлер для перезапуска сервиса
- скачивание rpm пакета за 3 попытки
- установка rpm пакета
- конфигурирование с использованием шаблонов из соответствующих yml.j2 файлов, расположенных в templates/
- вызов хендлера для перезапуска сервиса

Дополнения для filebeat:   
- подключение модуля system для сбора логов системы
- загрузка дашбордов

Также, для установки отдельных элементов стека, возможно использование ключа --tags с указанием необходимого компонента elasticsearch, kibana или filebeat.
