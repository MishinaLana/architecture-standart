### <a name="_b7urdng99y53"></a>**Название задачи:Task4 ADR Банк Стандарт** 
### <a name="_hjk0fkfyohdk"></a>**Автор: Мишина Светлана**
### <a name="_uanumrh8zrui"></a>**Дата: 09.07.2025**
### <a name="_3bfxc9a45514"></a>**Функциональные требования**
Опишите здесь верхнеуровневые Use Cases. Их нужно оформить в виде таблицы с пошаговым описанием:

| № | Действующие лица и системы          | Use Case                     | Описание |
|---|------------------------------------|------------------------------|----------|
| 1 | Сотрудник бэк-офиса, Сервис ставок | Выгрузка ставок для партнера | 1. Сотрудник запускает процесс выгрузки<br>2. Система формирует файл <br>3. Файл передается на сервер партнера |
| 2 | Сотрудник партнерского центра, партнерский кол-центр | Просмотр депозитов в системе | 1. Сотрудник авторизуется в системе партнерского кол-центра<br>2. Переходит в раздел "Депозиты"<br>3. Система показывает актуальные ставки |


### <a name="_u8xz25hbrgql"></a>**Нефункциональные требования**

|**№**|**Требование**|
|---|----------------|
| R   | Надёжность (Reliability) |
| R1  | Шифрование данных |
| R2  | Доступность SFTP-сервера 99.9% |
| P   | Производительность (Performance) |
| P1  | Обновление ставок в кол-центре менее 1 часа |
| P2  | Выгрузка файлов раз в сутки |


### <a name="_qmphm5d6rvi3"></a>**Решение**
Приведите диаграммы контекста и контейнеров в модели C4. Опишите там основные компоненты и интеграции всех элементов решения. 

[Контекстная диаграмма](https://www.planttext.com?text=ZLHFQnDH4By7yXsUUr9ewIL7aKAeDw7OtikQFYHqkvNa5UejcnGLgeYUn4DBGV2Qf7bckt7Jhp3pZVpDR3P_cXOaaCrxpFp-pMossovikTFZg5fvqemRqUcXDS_hjQrwxQ1-4ZjxvbvKAzMAQxh86lf9KygvIvuoJl3CgSzV3OqefJxTS0VVV_7fc_smVLIJnbtRQf_4JnjHqyPkmmI0cA3Q2qmWvryuZIdbZ-GveGm4taW9Vw1fy6m144RHgp0EtzgMT5tJbBlSuHwuSo1aHbidcsXJRD6Y-9SqK5q3IEto1GtnstFNW1JQSSmeNU9v4pQE7Y4Oy1VADd5_3dN93Fux86-qxiyCM8Ffhm6_Gynn8VuAp1rDp-CffbEwNJSG5759uWdm9_mPFQbogO5iaIIAXi9LhUozRpjx31knslW69Rc8lrPHETmeTr1uJ5Mirv69OOormnTAesFrT0Te6SyQnS7EcIjD5JSFGDujEoqJqzCdJVKXryhnsaRpdIczNCwJdM1mgpFatjP2_sB6Amu4MN6NLwa4lu8-EDI9t0UdT4DEGnc50Ar4pxqIjrYTEI2gHr2aa5YEqIDxLtHAp_qmzrxkx_xdZWd8VC7MXl83EoOfO8DeFDkU5GGf-gqwFOqDdEax3iPpNDno8XJRDZx4tyG_)

[Диаграмма контейнеров](https://www.planttext.com?text=ZLRBRjDG4Dr7oZzSig48qcxA3Y58KbGGfQ4Ei4HEUW63SIB7HI24r0Sl2H0FiK0iA1Mm9WsOkacT_iBuZvYPQplNSNYqKcMxdZDppZrpaZDTptIzjRjsiN34SbhssgeKfwhpSzNvwzMsuvcM8ztJnKAnu5cUBGMyXm1wy2DQnxy7-DiJC80HXD4c-B0F8VZuhn7qHSFitfcdmhfqksrdfcLRql5EY19yX262-5HJelklUBS7GVGCQpSOpHVqIlGKHgLZOm3JjfTCnxmfNQhQWL6q6Qr7M_0JkmOmK8CCorZ6s3GYut-2NHvt5thuz0NqyTgFDWKsxKMlyNO0WTQdQRRk_A71RlGA1cLy_XYdsuZXto7a3txlLmmSRQ0QlHnm1uLsrF3Rs7aTNsAvc7G0-ta29IKNoRk1-CFe9TO4t8i93CPAakRKgrWm7dGzUVTwfRtch9hk0-JZC9-tE598B7PukX1fyH2bO-9XiI3m9ptmcQxbIQL13_QfqwugLfJhYtLnNAn8i-NDtkxoaDkeC4roC5Pr10CQA0jiEPvq7UbLug4-AETWDKcnMKuQ4UXPepvxQQ4XbgvMnVpioVWiG-JS8wULaO0FXzY7p8C7c-z6bgbAQgd817mo_jYsURTSCE-PmkYubdDJLDfjRy91Q0bIuHyipMQNojwWvZi4K9DsvvQ5cYsxPikMZFaTVjAc24GuP05wE0gw88_ccfuqf7lFQiLdGc_tYSpOQICb6UjLRRkgnHSuvB7xA9dF7lPrRz821qcxYQQrvaoRPwqr4KcDBMgLaXhW2n9xpzVVk46OmfEfy3ACNaHFSamGbBWmv98XZCiN_ucN8PXJfdl3wv0oVBx6kKQzZBkarF7LzYntf6COYyaf8cD4HbI1ecihYF071Fz8Mw25-rwoikh950zbGU8yuBldJ63QJlEI7XNm2MSDQMr9BQOAVRGKchbOM95s6fZnBYus6dL3yKX56UBxsIIBjWXVBv_OE1q6hOpJQu6OMQWKIC_Tp4QDiJwdov4ae9wkgT48JiLhrjFNP5DSEL-A0u6JFz1phfz6x9vECGEIyyAVmlannyTGvGN1w9MJ1vu2RVC9--plMAlOwE0dG6d0JwBe_F2OIMBCSjYB-Kr-Nh0zq4RH5kSIxKAo3Ob5j4IEIR1BCiUpic0qviPdb6CmpJHQlGenO_biNGD1_-DSJtXZmlXpEpscAP9atJSLadoOvjHV3Ct5MYZLByub2PBFPnNeE0q28KYQh3dRf85qeLQf_bS4dP7EAdvV-Wq0)


**Логика принятия решений**

Минимизация изменений: 
- Использование существующего сервиса ставок
- Поддержка текущего стека технологий

Безопасность:
- Шифрование для файлов
- Изолированный SFTP-сервер

Масштабируемость:
- REST API для внутренних систем
- Пакетная выгрузка для внешних партнеров

**Альтернативы**

Прямое API для партнера:
+ Реальное время обновления
- Не поддерживается партнером

Ручная выгрузка XLS:
+ Простота реализации
- Риск человеческих ошибок

**Риски и ограничения**

Задержка данных у партнера:
Неактуальность 24 часа

Мониторинг:
Нужен контроль успешности выгрузок