# forJenkins
Стояла задача используя связку GIt + Jenkins + Docker (Docker compose) нужно получить следующий результат:
Появляется коммит в гит (гитхаб), затем собирается контейнер с Wordpress с вашими правками. 

План реализации:
1. Создание проекта на Git/Github.
2. Установка и настройка Jenkins на связь с Github, чтобы по коммиту Jenkins делал pull проекта из Github.
3. Настраиваем Docker и интегрируем с Jenkins, проводим тест по разворачиванию контейнера на node (slave) из Jenkins.
4. Создаем item в Jenkins, который объединяет предыдущие два пункта: по коммиту в Github Jenkins должен делать pull проекта из Github + 
создаем docker-compose.yml, в котором описаны сборки контейнеров с БД (Mysql), вебсервером (Nginx), Wordpress, запуск контейнеров.
5. Тестируем: изменяем index.html, делаем коммит и проверяем изменения сайта Wordpress.
