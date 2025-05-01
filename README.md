# 05-virt-04-docker-in-practice-ANMoiseenko
05-virt-04-docker-in-practice-ANMoiseenko

Задача 1\
\
1.Сделайте в своем github пространстве fork репозитория netology-code/shvirtd-example-python.\
\
Решение:\
![image](https://github.com/user-attachments/assets/954c3097-b5ae-4304-a1d8-f6277ce215a2)  

[Ссылка на репозиторий GitHub](https://github.com/joyspride812/shvirtd-example-python.git)
  
2.Создайте файл с именем Dockerfile.python для сборки данного проекта(для 3 задания изучите https://docs.docker.com/compose/compose-file/build/ ). Используйте базовый образ python:3.9-slim. Обязательно используйте конструкцию COPY . . в Dockerfile. Не забудьте исключить ненужные в имадже файлы с помощью dockerignore. Протестируйте корректность сборки.\
\
Решение:\
![image](https://github.com/user-attachments/assets/73f717d3-1440-4815-9b87-e3f7c9dc939e)

\
![image](https://github.com/user-attachments/assets/4115a18e-fee5-407d-ae15-6a0cb4562624)
\
\
![image](https://github.com/user-attachments/assets/6734e3e2-55fd-4594-8265-0dbeaf6fcca8)




Задача 3\
1.Изучите файл "proxy.yaml"\
2.Создайте в репозитории с проектом файл compose.yaml. С помощью директивы "include" подключите к нему файл "proxy.yaml".\
3.Опишите в файле compose.yaml следующие сервисы:\
web. Образ приложения должен ИЛИ собираться при запуске compose из файла Dockerfile.python ИЛИ скачиваться из yandex cloud container registry(из задание №2 со *). Контейнер должен работать в bridge-сети с названием backend и иметь фиксированный ipv4-адрес 172.20.0.5. Сервис должен всегда перезапускаться в случае ошибок. Передайте необходимые ENV-переменные для подключения к Mysql базе данных по сетевому имени сервиса web\

db. image=mysql:8. Контейнер должен работать в bridge-сети с названием backend и иметь фиксированный ipv4-адрес 172.20.0.10. Явно перезапуск сервиса в случае ошибок. Передайте необходимые ENV-переменные для создания: пароля root пользователя, создания базы данных, пользователя и пароля для web-приложения.Обязательно используйте уже существующий .env file для назначения секретных ENV-переменных!\

4.Запустите проект локально с помощью docker compose , добейтесь его стабильной работы: команда curl -L http://127.0.0.1:8090 должна возвращать в качестве ответа время и локальный IP-адрес. Если сервисы не стартуют воспользуйтесь командами: docker ps -a  и docker logs <container_name> . Если вместо IP-адреса вы получаете NULL --убедитесь, что вы шлете запрос на порт 8090, а не 5000.

Подключитесь к БД mysql с помощью команды docker exec -ti <имя_контейнера> mysql -uroot -p<пароль root-пользователя>(обратите внимание что между ключем -u и логином root нет пробела. это важно!!! тоже самое с паролем) . Введите последовательно команды (не забываем в конце символ ; ): show databases; use <имя вашей базы данных(по-умолчанию example)>; show tables; SELECT * from requests LIMIT 10;.

Остановите проект. В качестве ответа приложите скриншот sql-запроса.\
\
Решение:\
![image](https://github.com/user-attachments/assets/4efe0077-4c92-439d-ae07-72eb890ce6a4)  
\
\
Задача 4\
1.Запустите в Yandex Cloud ВМ (вам хватит 2 Гб Ram).\
2.Подключитесь к Вм по ssh и установите docker.\
3.Напишите bash-скрипт, который скачает ваш fork-репозиторий в каталог /opt и запустит проект целиком.\
4.Зайдите на сайт проверки http подключений, например(или аналогичный): https://check-host.net/check-http и запустите проверку вашего сервиса http://<внешний_IP-адрес_вашей_ВМ>:8090. Таким образом трафик будет направлен в ingress-proxy. ПРИМЕЧАНИЕ: приложение main.py( в отличие от not_tested_main.py) весьма вероятно упадет под нагрузкой, но успеет обработать часть запросов - этого достаточно. Обновленная версия (main.py) не прошла достаточного тестирования временем, но должна справиться с нагрузкой.\
5.(Необязательная часть) Дополнительно настройте remote ssh context к вашему серверу. Отобразите список контекстов и результат удаленного выполнения docker ps -a  
В качестве ответа повторите sql-запрос и приложите скриншот с данного сервера, bash-скрипт и ссылку на fork-репозиторий.  
\
Решение:\
\
![image](https://github.com/user-attachments/assets/afcd8839-9ccf-40c6-8f01-e68b9b54dac6)  
\
[bash скрипт](https://github.com/joyspride812/shvirtd-example-python/blob/main/shvirtd-example-python.sh)  
[Ссылка на fork-репозиторий](https://github.com/joyspride812/shvirtd-example-python.git)  

  
Задача 6\
Скачайте docker образ hashicorp/terraform:latest и скопируйте бинарный файл /bin/terraform на свою локальную машину, используя dive и docker save. Предоставьте скриншоты действий .\
\
Решение:\
\
![image](https://github.com/user-attachments/assets/53d2e7dd-dac8-4784-801d-afd3293cf075)  
![image](https://github.com/user-attachments/assets/b1de9a14-887f-48ed-ae5e-baae9d7c3a78)  
![image](https://github.com/user-attachments/assets/c9fc6e5f-d56f-413b-ad35-f1c951eadbc1)  
![image](https://github.com/user-attachments/assets/4d36e432-84b9-4cee-a0d4-9ded641dacac)  
\





Задача 6.1\
Добейтесь аналогичного результата, используя docker cp.\
Предоставьте скриншоты действий .\
\
Решение:\





