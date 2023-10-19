# ЗАДАЧА
Cоздать сервис, состоящий из 2 различных контейнеров: 1 - веб, 2 - БД (compose)

[Листинг консоли](hw5.txt)

Создаем и запускаем контейнер MYSQL (указываем его имя и в окружении задаем пароль):

![Screenshot_676.png](Screenshot_676.png)

Создаем и запускаем контейнер PHPMYADMIN с указанием связки LINK с конейнером mysql как сервис db (указываем его имя и проброс порта):

![Screenshot_677.png](Screenshot_677.png)

Смотрим IP:

![Screenshot_678.png](Screenshot_678.png)

Пробуем подключится в веббраузере к phpmyadmin:

![Screenshot_679.png](Screenshot_679.png)

Создаем директорию testcompose:

![Screenshot_682.png](Screenshot_682.png)

И в ней создаем YAML файл docker-compose.yaml:

![Screenshot_683.png](Screenshot_683.png)

Переходим cd в эту диреторию и запускаем docker-compose up -d:

![Screenshot_686.png](Screenshot_686.png)

Смотрим запущенные контейнеры:

![Screenshot_687.png](Screenshot_687.png)

Пробуем подключится к adminer:

![Screenshot_688.png](Screenshot_688.png)
![Screenshot_690.png](Screenshot_690.png)

# Задание со звездочкой - повышенной сложности..
Необходимо создать 3 сервиса в каждом окружении (dev, prod, lab)
по итогу на каждой ноде должно быть по 2 работающих контейнера

Создаем 3 ноды:

![Screenshot_686.png](swarm%2FScreenshot_686.png)
![Screenshot_687.png](swarm%2FScreenshot_687.png)
![Screenshot_688.png](swarm%2FScreenshot_688.png)

Инициализируем SWARM на главной ноде:

![Screenshot_690.png](swarm%2FScreenshot_690.png)

Добавляем остальные ноды как WORKER командой полученной при инициализации SWARM:

![Screenshot_691.png](swarm%2FScreenshot_691.png)
![Screenshot_692.png](swarm%2FScreenshot_692.png)

Смотрим список нод в SWARM

![Screenshot_693.png](swarm%2FScreenshot_693.png)

Смотрим список STACKов (стек по сути сборка наших сервисов в YAML файле)

![Screenshot_694.png](swarm%2FScreenshot_694.png)

Стеков нет.
Создаем YAML файлы для наших стеков:

Создаем директорию:

![Screenshot_695.png](swarm%2FScreenshot_695.png)

Создаем 3 YAML файла для наших стеков в разном окружении:

![Screenshot_709.png](swarm%2FScreenshot_709.png)

Деплоим стеки:

![Screenshot_696.png](swarm%2FScreenshot_696.png)

SWARM автоматически раскидал сервисы по нодам. Видим по 2 запущенных сервиса на каждой ноде.

![Screenshot_698.png](swarm%2FScreenshot_698.png)
![Screenshot_697.png](swarm%2FScreenshot_697.png)

Заходим в каждый стек по портам 6080, 6081, 6082 и создаем в каждом стеке свою базу данных:

![Screenshot_706.png](swarm%2FScreenshot_706.png)
![Screenshot_707.png](swarm%2FScreenshot_707.png)
![Screenshot_708.png](swarm%2FScreenshot_708.png)