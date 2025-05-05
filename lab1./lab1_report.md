University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FTMI](https://ftmi.itmo.ru/)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/) 

Group: U4125

Author: Demianko Aleksandra Sergeevna

Lab: Lab1

Date of create: 05.05.2025

Date of finished: 05.05.2025

***

1. Зайдите в вкладку IAM, создайте service account с ролью Storage Admin.

В качестве нейминга используйте первую букву имени и фамилию, а также добавьте -sa-lab1. Например Ivan Filianin = ifilianin-sa-lab1.

![Alt text](../storageAdmin.png?raw=true "Storage Admin Account")


2. Создать минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot.

В качестве нейминга используйте первую букву имени и фамилию, а также добавьте -vm-lab1. Например Ivan Filianin = ifilianin-vm-lab1.

3. С помощью утилиты gsutils найдите бакет lab1-bucket-itmo и скопируйте 3 файла в локальную папку на VM. Используя команду ls -lah отобразите что эти файлы хранятся у вас на VM.

4. Поменяйте права доступа для вашего service account с Storage Admin на Compute Viewer, попробуйте повторить пункт с копированием данных, сделать выводы.

5. Удалите за собой все созданные сервисы, напишите отчет с использованием скриншотов.
