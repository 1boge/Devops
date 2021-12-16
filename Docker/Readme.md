Задание:

Необходимо сделать dockerfile для получения рабочего контейнера.

    В качестве основы, берём образ continuumio/miniconda3:latest
    Добавляем и делаем рабочей папкой /app
    Создаём простой sh файл с названием 1.sh, который должен выдавать надпись “Hello Netology”.
    Надо скопировать этот файл внутрь контейнера и выдать ему права на исполнение.
    Запустить установку пакетов python mlflow boto3 pymysql.
    В конце запустить на вывод файл 1.sh.
    После чего собрать через docker build контейнер с тегом netology-ml:netology-ml

Домашнее задание выполните в файле readme.md в github репозитории.


Решение:

# Создание образа

alexey@Air-Alexey Devops % docker build -t netology-ml:netology-ml .
[+] Building 16.2s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                            0.0s
 => => transferring dockerfile: 2.34kB                                                                          0.0s
 => [internal] load .dockerignore                                                                               0.0s
 => => transferring context: 2B                                                                                 0.0s
 => [internal] load metadata for docker.io/continuumio/miniconda3:latest                                        0.5s
 => [internal] load build context                                                                               0.0s
 => => transferring context: 25B                                                                                0.0s
 => CACHED [1/6] FROM docker.io/continuumio/miniconda3:latest@sha256:592a60b95b547f31c11dc6593832e962952e3178f  0.0s
 => => resolve docker.io/continuumio/miniconda3:latest@sha256:592a60b95b547f31c11dc6593832e962952e3178f1fa11db  0.0s
 => [2/6] RUN apt-get update --fix-missing &&     apt-get install -y wget bzip2 ca-certificates curl git bash&  2.4s
 => [3/6] RUN pip install mlflow boto3 pymysql                                                                 12.0s
 => [4/6] WORKDIR /app                                                                                          0.0s
 => [5/6] COPY ./1.sh /1.sh                                                                                     0.0s
 => [6/6] RUN chmod +rx /1.sh                                                                                   0.2s
 => exporting to image                                                                                          1.0s
 => => exporting layers                                                                                         1.0s
 => => writing image sha256:0de10ae3c00c6edd7c68e17558f50ddac64ec1c266bdbe82a4920ae27ee48643                    0.0s
 => => naming to docker.io/library/netology-ml:netology-ml                                                      0.0s
 
 # Запуск контейнера
 
alexey@Air-Alexey Devops % docker run -d --name netology-ml netology-ml:netology-ml
5a144c4ad0676430dd53eebb32659ade82a66108275d6306f4a4142fac18d4ac
alexey@Air-Alexey Devops %

![изображение](https://user-images.githubusercontent.com/67161186/146450323-ae62cb90-f296-458e-b72c-f2bfe178d399.png)
