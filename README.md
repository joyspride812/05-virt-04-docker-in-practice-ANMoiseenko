# 05-virt-04-docker-in-practice-ANMoiseenko
05-virt-04-docker-in-practice-ANMoiseenko

Задача 1\
\
1.Сделайте в своем github пространстве fork репозитория netology-code/shvirtd-example-python.\
\
Решение:\
![image](https://github.com/user-attachments/assets/954c3097-b5ae-4304-a1d8-f6277ce215a2)\
2.Создайте файл с именем Dockerfile.python для сборки данного проекта(для 3 задания изучите https://docs.docker.com/compose/compose-file/build/ ). Используйте базовый образ python:3.9-slim. Обязательно используйте конструкцию COPY . . в Dockerfile. Не забудьте исключить ненужные в имадже файлы с помощью dockerignore. Протестируйте корректность сборки.\
\
Решение:\
![image](https://github.com/user-attachments/assets/73f717d3-1440-4815-9b87-e3f7c9dc939e)

\
![image](https://github.com/user-attachments/assets/c7bb93f9-93bf-4425-9df3-26792c2200fd)\
\
![image](https://github.com/user-attachments/assets/6734e3e2-55fd-4594-8265-0dbeaf6fcca8)

\
![image](https://github.com/user-attachments/assets/d30c4c48-e708-4451-939c-74c66498ce65)
\
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




