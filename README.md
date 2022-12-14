# forJenkins
Стояла задача: используя связку GIt + Jenkins + Docker (Docker compose) нужно получить следующий результат:
при появлении коммита в гит (гитхаб) собирается контейнер с Wordpress с вашими правками. 

План реализации:
1. Создание проекта на Git/Github.
2. Устанавливаем и настраиваем Jenkins на связь с Github и node (slave), чтобы по коммиту в Github Jenkins делал pull проекта из Github на node.
3. Устанавливаем Java, Docker, Docker-compose, Git на node:<br/>
>sudo apt update<br/>
>sudo apt install openjdk-11-jre -y<br/>
>java -version<br/>
>curl -fsSL https://get.docker.com -o get-docker.sh<br/>
>sudo sh get-docker.sh<br/>
>sudo usermod -aG docker $USER<br/>
>sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose<br/>
>sudo chmod +x /usr/local/bin/docker-compose<br/>
>docker-compose --version<br/>
>sudo apt install git<br/>
>
затем интегрируем с Jenkins, проводим тест по разворачиванию контейнера на node из Jenkins.<br/>
>sudo -i<br/>
>\# ssh-keygen -f ~/.ssh/jekins_agent_key<br/>
>\# cat ~/.ssh/jekins_agent_key.pub > ~/.ssh/authorized_keys<br/>
>\# cat ~/.ssh/jekins_agent_key<br/>
>
вывод команды копируем в jenkins credentials ssh-key

4. Создаем item в Jenkins, который объединяет предыдущие два пункта: по коммиту в Github Jenkins должен делать pull проекта из Github + 
создаем docker-compose.yml, в котором описаны сборки контейнеров с БД (Mysql), вебсервером (Nginx), Wordpress, запуск контейнеров.
5. Тестируем: изменяем index.html, делаем коммит и проверяем изменения сайта Wordpress.

Итог:
![image](https://user-images.githubusercontent.com/97964258/200326883-43f369ea-ad79-4ef8-8298-5c3ad1959455.png)
![image](https://user-images.githubusercontent.com/97964258/200327135-9a7216e6-1628-49fc-a110-635e417ffdfe.png)
