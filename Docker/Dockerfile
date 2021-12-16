FROM continuumio/miniconda3:latest
LABEL maintainer="Myself"
# Устанавливаем зависимости
RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates curl git bash&& \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
# Устанавливаем пакеты Питона
RUN pip install mlflow boto3 pymysql
# Задаём текущую рабочую директорию
WORKDIR /app
# Копируем код из локального контекста в рабочую директорию образа
COPY ./1.sh /1.sh
# Задаём значение по умолчанию для переменной
#ARG my_var=my_default_value
#Даем права доступа
RUN chmod +rx /1.sh

# Настраиваем команду, которая должна быть запущена в контейнере во время его выполнения
ENTRYPOINT ["bash", "/1.sh"]
# Copy Scripts
#COPY ./start.sh /start.sh

#EXPOSE 80

#CMD ["/start.sh"]

#CMD  ["/1.sh"]
# Открываем порты
#EXPOSE 8000
# Создаём том для хранения данных
#VOLUME /experiment


#FROM debian:latest

#  $ docker build . -t continuumio/miniconda3:latest -t continuumio/miniconda3:4.5.11
#  $ docker run --rm -it continuumio/miniconda3:latest /bin/bash
#  $ docker push continuumio/miniconda3:latest
#  $ docker push continuumio/miniconda3:4.5.11

#ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
#ENV PATH /opt/conda/bin:$PATH

#RUN apt-get update --fix-missing && \
 #   apt-get install -y wget bzip2 ca-certificates curl git && \
  #  apt-get clean && \
   # rm -rf /var/lib/apt/lists/*

#RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
 #   /bin/bash ~/miniconda.sh -b -p /opt/conda && \
 #   rm ~/miniconda.sh && \
 #   /opt/conda/bin/conda clean -tipsy && \
 #   ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
 #   echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
 #   echo "conda activate base" >> ~/.bashrc

#ENV TINI_VERSION v0.16.1
#ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
#RUN chmod +x /usr/bin/tini

CMD [ "1.sh" ]
#ENTRYPOINT [ "/usr/bin/tini", "--" ]
#CMD [ "/bin/bash" ]