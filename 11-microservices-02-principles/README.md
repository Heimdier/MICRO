## Задача 1: API Gateway 

Предложите решение для обеспечения реализации API Gateway. Составьте сравнительную таблицу возможностей различных программных решений. На основе таблицы сделайте выбор решения.

Решение должно соответствовать следующим требованиям:
- Маршрутизация запросов к нужному сервису на основе конфигурации
- Возможность проверки аутентификационной информации в запросах
- Обеспечение терминации HTTPS

Обоснуйте свой выбор.

## Задача 2: Брокер сообщений

Составьте таблицу возможностей различных брокеров сообщений. На основе таблицы сделайте обоснованный выбор решения.

Решение должно соответствовать следующим требованиям:
- Поддержка кластеризации для обеспечения надежности
- Хранение сообщений на диске в процессе доставки
- Высокая скорость работы
- Поддержка различных форматов сообщений
- Разделение прав доступа к различным потокам сообщений
- Протота эксплуатации

Обоснуйте свой выбор.

---
## Задача 1: API Gateway 

Для реализации API Gateway в микросервисной архитектуре можно рассмотреть следующие решения:

1. **NGINX plus**
2. **Kong Gateway**
3. **AWS API Gateway**
4. **Apigee (Google Cloud)**
5. **Azure API Management**

**Ниже сравнительная таблица характеристик:**

| **Характеристика**               | **NGINX Plus**                      | **Kong Gateway**                     | **AWS API Gateway**           | **Apigee (Google Cloud)**                        | **Azure API Management**                     |
|----------------------------------|-------------------------------|-------------------------------|-------------------------------|--------------------------------|--------------------------------|
| **Маршрутизация запросов по конфигурации**       | Да (гибкая настройка через конфигурационные файлы и политики) | Да (через декларативные правила и плагины) | Да (через API-спецификации) | Да (через прокси и политики) |Да (через маршруты и политики) |
| **Проверка аутентификации**      | Да (поддержка JWT, API ключей, OAuth через плагины и скрипты) | Да (поддержка OAuth2, JWT, API ключей) |Да (встроенные механизмы авторизации) |Да (через политики OAuth2, JWT) | Да (через политики OAuth2, JWT) |
| **Терминация HTTPS**             | Да | Да | Да | Да | Да |
| **Масштабируемость**             | Высокая, требует настройки и обслуживания | Высокая, открытый код | Высокая, полностью управляемый | Высокая, облачное решение | Высокая, облачное решение |
| **Сложность внедрения и поддержки** | Средняя (требует настройки и обслуживания) | Средняя (гибко, требует настройки) | Низкая (обслуживание полностью автоматизировано) | Средняя (облачная настройка) | Средняя (облачная настройка) |


***Итоги:***    
- NGINX Plus — хороший кандидат, если нужен настраиваемый API Gateway, который может эффективно обрабатывать маршрутизацию, аутентификацию и терминацию HTTPS.   
- Если предпочтение к полностью управляемому решению с минимальным обслуживанием, то подойдут AWS API Gateway или Azure API Management.      
- Если нужен вариант с открытым исходным кодом и высокой степенью настройки, подойдет Kong Gateway.

---
## Задача 2: Брокер сообщений    

**Cравнительная таблица основных брокеров сообщений:**   

| Брокер сообщений    | Поддержка кластеризации | Хранение сообщений на диске | Скорость работы | Поддержка различных форматов | Разделение прав доступа | Простота эксплуатации |
|---------------------|-------------------------|---------------------|------------------|-------------------------------|------------------------|-----------------------|
| **Apache Kafka**    | Да                      | Да                  | Очень Высокая    | JSON, XML, Protobuf и др.    | Да                      | Средняя               |
| **RabbitMQ**        | Да                      | Да                  | Высокая          | JSON, XML, текст и др.       | Да                      | Высокая               |
| **ActiveMQ**        | Да                      | Да                  | Высокая          | JSON, XML, текст и др.       | Да                      | Средняя               |
| **Amazon SQS**      | Да                      | Да                  | Высокая          | Огранчиченная (JSON, XML)    | Ограниченно             | Высокая               |
| **NATS Streaming**  | Нет                     | Нет                 | Очень Высокая    | Огранчиченная (JSON, XML)    | Нет                     | Высокая               |



### Обоснование выбора решения   
1. Надежность и кластеризация   
Все брокеры, кроме NATS Streaming, поддерживают кластеризацию, что обеспечивает отказоустойчивость и надежность.   
Для критичных систем предпочтительнее использовать Kafka, RabbitMQ или ActiveMQ Artemis.   
2. Хранение сообщений на диске   
Все вышеперечисленные брокеры, кроме NATS Streaming, обеспечивают хранение сообщений на диске, что важно для восстановления данных и надежности.   
3. Высокая скорость работы   
Kafka и NATS Streaming демонстрируют очень высокую скорость, особенно при больших объемах данных.   
RabbitMQ и ActiveMQ Artemis тоже показывают хорошую производительность, но чуть ниже.   
4. Поддержка различных форматов сообщений   
Все брокеры поддерживают стандартные форматы (JSON, XML).   
5. Разделение прав доступа   
Все выбранные брокеры позволяют реализовать разделение прав доступа к потокам сообщений через механизмы авторизации и аутентификации.   
6. Простота эксплуатации   
RabbitMQ и Amazon SQS считаются наиболее простыми в настройке и обслуживании.   
Kafka требует более сложной настройки, но обладает мощным функционалом.   
ActiveMQ Artemis — средний уровень сложности.
  
**Итоговый выбор**   Apache Kafka   
**Обоснование:**   

- Обеспечивает высокую надежность благодаря кластеризации и хранению сообщений.   
- Обладает очень высокой скоростью обработки данных.   
- Поддерживает различные форматы сообщений.   
- Позволяет реализовать разделение прав доступа.   
- При правильной настройке и наличии специалистов — подходит для систем с высокими требованиями к надежности и скорости.   


  
