University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FTMI](https://ftmi.itmo.ru/)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/) 

Group: U4125

Author: Demianko Aleksandra Sergeevna

Lab: Lab4

Date of create: 05.05.2025

Date of finished: 05.05.2025

***

## Цель проекта

Создание AI-сервиса *MedImageCheck* для загрузки и распознавания медицинских изображений с использованием Google Cloud. Приложение проходит три стадии: **MVP**, **Тестирование партнёрами**, **Продакшен**.

---

## 1. Архитектура

### 1.1 MVP (Минимально жизнеспособный продукт)

**Описание:**
- Frontend размещён как Web/Mobile клиент.
- Backend — на Cloud Run (автоскейлируемый).
- AI-модель вынесена в Vertex AI Custom Endpoint.
- Хранение — Cloud Storage (20 ГБ).
- Данные — Cloud SQL (db-g1-small).
  
**Схема:**  
![MVP](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/c63ccd0b06c80b8bc3e018d7342bdbd588405c80/lab4/mvp.png)

**Нагрузка:** ок. 10 пользователей в день, 1–5 rps.

**Затраты:**
| Компонент | Цена (USD) |
|-----------|------------|
| Cloud Run | 2.51       |
| Cloud SQL (db-g1-small) | 21.60 |
| Cloud Storage (20 GB) | 0.52 |
| **Итого** | **24.63** |

---

### 1.2 Тестирование партнёрами

**Изменения:**
- Переход на GKE Standard (вместо Cloud Run) для стабильности и тестов нагрузки.
- Подключены Cloud Monitoring и Logging.
- Хранение логов и аналитики — через BigQuery или Firestore.
- Нагрузка: 150 пользователей в день.

**Схема:**  
![Тестирование](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/c63ccd0b06c80b8bc3e018d7342bdbd588405c80/lab4/stg.png)

**Затраты:**
| Компонент | Цена (USD) |
|-----------|------------|
| GKE Standard (тестовая конфигурация) | ~20.00 |
| Cloud SQL (db-g1-small) | 21.60 |
| Cloud Storage (20 GB) | 0.52 |
| Vertex AI Endpoint | 136.80 |
| **Итого** | **178.92** |

---

### 1.3 Продакшен

**Изменения:**
- Backend продолжает работать на GKE Standard, но в продовой конфигурации.
- Cloud SQL увеличен до db-n1-standard-2.
- Добавлены: CI/CD (Cloud Build), BigQuery, мониторинг и логирование.

**Схема:**  
![Продакшен](https://github.com/alexandraDem/2024_2025-cloud-platforms-as-the-basis-of-technology-entrepreneurship-U4125-demyanko_a_s/blob/c63ccd0b06c80b8bc3e018d7342bdbd588405c80/lab4/prod.png)

**Нагрузка:** до 1000 пользователей в день.

**Затраты:**
| Компонент | Цена (USD) |
|-----------|------------|
| GKE Standard | 429.68 |
| Vertex AI | 136.80 |
| Cloud Storage (200 GB) | 5.20 |
| Cloud SQL (db-n1-standard-2) | 68.40 |
| Monitoring/CI/CD (в пределах бесплатного лимита) | 0.00 |
| **Итого** | **347.20** |

---

## 2. Обоснование архитектуры

- **Cloud Run** удобен для начального запуска.
- **Vertex AI Endpoint** — готовый хостинг для моделей без DevOps.
- **GKE** используется на тесте и в проде для гибкости и надёжного автоскейлинга.
- **BigQuery/Firestore** позволяют собирать и анализировать статистику по инференсам.
- **Cloud Monitoring** даёт метрики и оповещения.

