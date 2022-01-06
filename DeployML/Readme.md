Цель задания

Закрепить полученные знания и научиться настраивать PyTorch посредством настройки окружения и проведения обучения модели c использованием torchserve-dashboard
Задание:

    Устанавливаем и настраиваем conda либо python3
    Устанавливаем и настраиваем torchserve через pip3 либо conda
    Устанавливаем и настраиваем torchserve-dashboard через pip3 либо conda
    Загружаем обученную модель: wget https://download.pytorch.org/models/densenet161-8d451a50.pth
    Заархивируйте модель с помощью архиватора моделей.
    Стартуем сервер из под torchserve-dashboard с параметром --config_path ./torchserve.properties --model_store ./model_store --server.port 8501 -- --config_path ./torchserve.properties

Домашнее задание выполните в файле readme.md в github репозитории.
Результат:

В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории. Приложите:

    файл readme.md с выполненным заданием в репозитории Github
    Скриншот запущенного Torchserve Management Dashboard с запущенным сервером
