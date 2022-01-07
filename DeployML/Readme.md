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
    
   Pytorch_server:
![изображение](https://user-images.githubusercontent.com/67161186/148525363-a239a8d3-96f6-451c-b572-8f776120b03c.png)
![изображение](https://user-images.githubusercontent.com/67161186/148525552-c6890520-b64b-46c0-b468-8e4297a03dd6.png)
   Pytorch_dashboard:
![изображение](https://user-images.githubusercontent.com/67161186/148525457-46a7e38d-e889-4023-b4bb-92084dd6103d.png)
![изображение](https://user-images.githubusercontent.com/67161186/148526293-dfe2591f-8dc8-4e3b-97ef-51cd13ace587.png)

   Зарахивированная модель:
    
![изображение](https://user-images.githubusercontent.com/67161186/148525884-8fe607c7-7693-4c32-8aea-66596c861204.png)
    
   Доступная и зарегестрированная модель:    
![изображение](https://user-images.githubusercontent.com/67161186/148526019-8dd96f11-1972-4a40-889f-d799ea648764.png)
    
   Детали модели:
![изображение](https://user-images.githubusercontent.com/67161186/148526076-52e08d57-e55f-46cd-89e7-a419cf649e1a.png)
