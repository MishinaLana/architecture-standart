### <a name="_b7urdng99y53"></a>**Название задачи:Task3 ADR Банк Стандарт** 
### <a name="_hjk0fkfyohdk"></a>**Автор: Мишина Светлана**
### <a name="_uanumrh8zrui"></a>**Дата: 09.0.2025**
### <a name="_3bfxc9a45514"></a>**Функциональные требования**
Опишите здесь верхнеуровневые Use Cases. Их нужно оформить в виде таблицы с пошаговым описанием:

| № | Действующие лица и системы          | Use Case                     | Описание |
|---|------------------------------------|------------------------------|----------|
| 1 | Клиент, Сайт банка                 | Просмотр списка депозитов на сайте   | 1. Клиент заходит на сайт банка<br>2. Переходит в раздел "Депозиты"<br>3. Система отображает список доступных депозитов с актуальными ставками |
| 2 | Клиент, Сайт банка, Кол-центр      | Подача заявки на депозит     | 1. Клиент заполняет форму (ФИО, телефон)<br>2. Система сохраняет заявку<br>3. Кол-центр получает уведомление о новой заявке |
| 3 | Клиент, Интернет-банк              | Просмотр депозитов в интернет-банке      | 1. Клиент авторизуется в интернет-банке<br>2. Переходит в раздел "Депозиты"<br>3. Система показывает список депозитов с общими и персональными ставками |
| 4 | Клиент, Интернет-банк, СМС-сервис  | Оформление депозита          | 1. Клиент выбирает депозит, указывает счет и сумму<br>2. Система запрашивает SMS-подтверждение<br>3. Клиент вводит код из SMS<br>4. Система создает заявку на депозит |
| 5 | Менеджер бэк-офиса, АБС           | Управление ставками          | 1. Менеджер открывает раздел ставок в АБС<br>2. Вносит изменения в ставки<br>3. Система сохраняет изменения и синхронизирует с другими системами |
| 6 | Менеджер бэк-офиса, АБС, СМС-сервис | Согласование заявки        | 1. Менеджер проверяет заявку в АБС<br>2. Подтверждает условия депозита<br>3. Система отправляет SMS-уведомление клиенту |
| 7 | АБС, Система уведомлений           | Оповещение клиента           | 1. АБС фиксирует открытие депозита<br>2. Система уведомлений отправляет SMS клиенту<br>3. Клиент получает информацию об открытом депозите |
### <a name="_u8xz25hbrgql"></a>**Нефункциональные требования**
Опишите здесь нефункциональные требования и архитектурно значимые требования.

|**№**|**Требование**|
|---|----------------|
| R   | Надёжность (Reliability) |
| R1  | Шифрование трафика |
| R2  | Доступность 24/7, 99.9% |
| R3  | Переключение на резервный ЦОД при сбое |
| R4  | Регулярные бэкапы БД|
| P   | Производительность (Performance) |
| P1  | Загрузка списка депозитов менее 500 мс |
| P2  | Проведение операций менее < 1 сек |
| P3  | Горизонтальное масштабирование интернет-банка |
| P4  | Вертикальное масштабирование АБС|
| +R  | + Ограничения (Restrictions) |
| +R1 | Шифрование персональных данных |
| +R2 | Использование существующих решений |
| +R3 | Kafka для очередей |
| +R4 | Микросервисная архитектура |

### <a name="_qmphm5d6rvi3"></a>**Решение**
Приведите диаграммы контекста и контейнеров в модели C4. Опишите там основные компоненты и интеграции всех элементов решения. 

[Контекстная диаграмма](https://www.planttext.com?text=ZLJRIkDG57qlz1-EVNAWnHSVPH2AZuBe1vHO3r8cJQ4vWhxr8buG5SMdOR1qc0zeOwCnDV4NzlaZrpwdbwWj38Mc9zthijVUoQQldAOwghlvt4hDgxf71r9ibDVNokkLSiDJybZzpEVoELLJhXJqcr9AT8T2YdKRruG6-bRGY28Qq9DkuViDdm53TcJJRtYhLRScFLKK1O37g0kPeC3dVpYzKAJFATHjYa4T2YxHPvGM1QNWZtLBNr40bHjz2MZ8MY6zevQHdSAFkOxZkjkEvnpA9fFt6Gzq5u04Gh4m2kCIs8q5DcjiFDBG61z2fMFLOAWZe83cS8mfokZiEzLVImI6-fhY4kwVmbjxGj-3wWYj121jqJEg5zFdStidlf9r27X6u0w52TFsWUQVG4BFPjTd1JC8f9t92jV8JYIJ4gv1LgAoTQnM_RflYVvGlwGlQAnlwCK60iIxYIJ0tLlZ5csY0T2c41npWbOddizKTraZew2aAwkDEbF-HGcZU0HlI0ZUE8q1UzCjeteFoX0-ECjNWVYu8E0sRNjJHuXBMDUsfLtfpdPi6jsZoIRhVvwsxgvzNYtx_xUrChpPdPgIzs0ajUFyHavHaKy1FoPCj20WvhKxD2FypmsnICPCPhTeK0moDrCEBk7bc8N510QQcKpFY8PckUuORwgN-9xXvW_r0mjz3NiPnwRq3l2g-G00)

[Диаграмма контейнеров](https://www.planttext.com?text=dLPDRzj64BqBq7_OwEGYbNLnRqMGI3AQ15R3caAk0Iql4hOKbP1qKgCeu2YVW9Ec3Gma28AcRbhqMDgrQagowB-m-uyoCqikIL5EFsp09aNkc_TcthxLHJ-ml62hxrGhvsotvsnjSlPvQwNHMhdH6hY1PRlSkr2jL2k17JYSYJqHYL3y9NVWxmdyXanCH2ncSYX6OYncOWIFOd68Impk-GDtgUVOt0q-PJNnHanX-GZVhk7zRt1tB2Bv15RT9vmHmrVaOn7NFia0BCVfMAvratkuQb_4SYXtv0Dn1FKYCL4KfdLOHjX8Zl1_5WT4z424yEckE8JhaHmoA1hA5t0x4L6kpeRL--QC0WVokPZKuVE7mEv-0lyEgXw1y4CI_JUydS0V0OzJU8ZQXbYWMZ6t_O3tRpG7M-wcvMr3BPTg_GHhPbXX7u3m4a2WDAnYtrKh37xq69PyE-2ANoZ6MET0BLPqZCi6Ey_MkTKBbh_s5K6WXVq-oHJ7M2l6nJCSazoLZx1zUYxu8J8kLhRTW7ik3ve9wzTgu02F0n_MKoPOzP9fB7-vscMTwossilnPCeWPb0ZH8DZ4ePY0nbtu7-742-rQIA2z0IRetIBrR-Hp-HHqRjeayefRx_F-mDkkwOS0GnuaJbW19dPAHW3zOBQPKdr4p-cch1Wzr-8eMtKSfauMruuls-sgTTTYvctFTc-ovc0Gp5cGPEFgt2ZATQqD7vVz2CROHu0sTsxVic6mrpohvt32_1DS1mAp-UCWSVz4A2k6Nk9aGk0NYV6YNWu8gxq1O0gMjPirfVCz5DwZwz-9zmmrfcFI_IfPXedetynnoRC2RdBlhjrBd8nC3x6xZ1eS9ds1XsWY8l9U3s-goUYN9vH3KFmK6r9a04yMgVVlE2IzOpBpgxL_rXs2MuSG1g6OocU9_WBPaag_xty1GkzPsmhyhTYlWosdyWTnNClj7vMZDATOjLQCqQnJk1qh-y1hgNeq3z20j06TCQXEsq4p_ZwNCglV1ai1TtXlq4UGN-4zV1UDSbBF6GI697UepalQo4yL75B8vgBugnHRvuwEyoIDBdUxXfbmJPio1NyNSrO-G83yyhb8oSCayP35TIbF4KZLB-pJzLMpsyYGtf6AKPRB2-WKQHJjEGVt2c1e5fWmcbpEYT5Yq3IvT6I9FsZuPAy6aW9nc2_FO5jHVeNp6lytG9692XVpsYMZKUottc0V6rokqmk182J1meyeUsV9oOw7Q3B293p4A0-eZ_N273FCNtHqfjtE7zwqzLCuTNehPabgjiXh_-6ibhif6k4Kzl6S6rwZHjgwEPLwgz3mSgkptMXs3EFilXS0z2Bz3ShigE9xq9BvpROm6aRPlYruEyt0g-rcQs7gpGTS2K4rUhMxTiRiATRaYz8ngvkREuICjKQQnENpKXsm075CIQmFjOlStOJlhHy0)


**Логика принятия решений**

Защита данных:
 - Используется HTTPS для всех внешних и внутренних API
 - Шифрование трафика между системами (например, REST/SOAP + TLS)

Интеграция с АБС:
- Устраняется прямая интеграция интернет-банка и АБС из-за нагрузки
- Используется промежуточный слой API-шлюз

СМС-уведомления:
- Используется существующий СМС-шлюз во избежание доработок ядро

Хранение ставок:
- Перенос ставки из XLS в АБС с REST API для доступа из других систем

Масштабируемость:
- Интернет-банк: горизонтальное масштабирование (ASP.NET + MS SQL).
- АБС: только вертикальное (Oracle + PL/SQL).

Резервирование:
- Переключение на резервный ЦОД

**Альтернативы**

Микросервисы для интернет-банка:
Плюсы: Гибкость, независимое масштабирование
Минусы: Сложность интеграции с текущим монолитом, требует Kafka (несовместимо сейчас)

Kafka для асинхронной обработки заявок:
Плюсы: Уменьшает нагрузку на АБС
Минусы: Требует обновления интернет-банка

GraphQL вместо REST:
Плюсы: Гибкость запросов
Минусы: Нет экспертизы в банке

**Риски и ограничения**

Нагрузка на АБС:
- При большом потоке заявок возможны задержки

Отказоустойчивость интернет-банка:
- Сейчас нет автоматического переключения на резервный ЦОД

Зависимость от подрядчиков:
- Обновление ядра интернет-банка и кол-центра требует участия вендоров

СМС-шлюз:
- Задержки отправки уведомлений из-за внешнего оператора