# "Репликация и масштабирование. Часть 1" - Горегляд Николай

### Задание 1. 

`На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.`


##### ответ:

`Режим master-slave - это репликация данных которая увеличивает доступность данных хранимых на основном сервере путем копии данных в slave и возможности пользователям считывать данные не с основного сервера БД, данные вычитываются из журнала WAL логов транзакций mastera. Также присутствует возможность сменить master при его отказе, тогда у slave появится возможность записывать данные в БД`

`в режиме master-master появляется избыточность репликации при которой оба сервера могут писать данные в БД синхронизируя данные для их целостности, если один из master выключится, второй возмет на себя всю нагрузку не требуя дополнительных переключений режима.`

### Задание 2. 

`Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.`

##### ответ:
`Как было предложено в конце лекции попробовал выполнить конфигурацию на Postgre`

`на первом скриншоте представлены настройки и страрт репликации` 
 ![Task-2-1](https://github.com/nick-mp/postgres-replica-docker/blob/main/postgres-replication/img/replication%20start.png)

`на этом скриншоте видно репликацию данных при создании таблицы на сервере master` 
 ![Task-2-2](https://github.com/nick-mp/postgres-replica-docker/blob/main/postgres-replication/img/show_replication.png)

 `После "неудачной" попытки создать таблицу со slave сервера, произведена остановка сервера master и переключен режим на сервере slave на master` 
 ![Task-2-3](https://github.com/nick-mp/postgres-replica-docker/blob/main/postgres-replication/img/stop_master_change_to_slave.png)

 `На бывшем сервере slave, ставшим master произведено добавление новой таблицы` 
 ![Task-2-4](https://github.com/nick-mp/postgres-replica-docker/blob/main/postgres-replication/img/add_table_from_postgres-2(replica).png)