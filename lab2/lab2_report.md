University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FTMI](https://ftmi.itmo.ru/)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/) 

Group: U4125

Author: Demianko Aleksandra Sergeevna

Lab: Lab2

Date of create: 05.05.2025

Date of finished: 05.05.2025

***

1. Создайте Cloud Run из представленного дефолтного сервиса Hello с минимальным количеством ресурсов.Важно! Если у вас есть ваш сервис, лучше использовать его, будет полезнее и интереснее

Создаем сервис
![create](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/35d639f995d9c52f3b5c45ea373b69281292d2ba/lab2/createservice.png)

Ставим минимальные настройки
![sett](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/35d639f995d9c52f3b5c45ea373b69281292d2ba/lab2/settings.png)


2. Перейдите по ссылке предоставленной Cloud Run, протестируйте сервис.

Переходим по эндпоинту и видим работающий сервис
![service](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/35d639f995d9c52f3b5c45ea373b69281292d2ba/lab2/running.png)
   
4. Перейдите в разделы логи и метрики, проанализируйте их.

В логах видим создание нашего сервиса и несколько успешных GET запросов
![a](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/c057b36443dee8e11fe7686dff46639f69f352a6/lab2/logs1.png)

В метриках также видим трафик от нескольких запросов 
![a](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/c057b36443dee8e11fe7686dff46639f69f352a6/lab2/metrics1.png)
  
5. Измените ваш Cloud Run, поменяв порт на 8090, посмотрите что произойдет. Попробуйте попереключать трафик между версиями, сравните результаты работы.

![image](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/361a2682ee45df72133f3d370939aa5676610607/lab2/traffic.png)

Далее смотрим за изменениями в логах:

- Контейнер теперь запускается и слушает порт 8090 вместо 8080.
- Произошло обновление сервиса (ReplaceService), после чего контейнер выводит сообщение о старте на новом порту.

CPU/Memory Utilization: минимальные нагрузки, стабильные показатели (CPU около 1%, память около 10-20%).
Container Startup Latency: небольшая задержка старта контейнера (примерно 80 мс).
Max Concurrent Requests: максимум 2 одновременных запроса во время переключения

Изменения по метрикам:
- Container Instance Count увеличился до двух в момент переключения.
- Max Concurrent Requests 2 во время переключения.

![image](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/361a2682ee45df72133f3d370939aa5676610607/lab2/containerInstanceCount.png)

   
8. Удалить за собой все созданные сервисы, написать отчет с использованием скриншотов.
